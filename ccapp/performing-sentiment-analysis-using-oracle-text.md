Sentiment analysis enables you to identify a positive or negative sentiment in a search topic.

This chapter contains the following topics:

- Overview of Sentiment Analysis

- Creating a Sentiment Classifier Preference

- Training Sentiment Classifiers

- Performing Sentiment Analysis with the CTX_DOC Package

- Performing Sentiment Analysis with the RSI

### 16.1 Overview of Sentiment Analysis

Sentiment analysis uses trained sentiment classifiers to provide sentiment information for documents or topics within documents.

This section contains the following topics:

- About Sentiment Analysis

- About Sentiment Classifiers

- About Performing Sentiment Analysis

- Sentiment Analysis Interfaces

#### 16.1.1 About Sentiment Analysis

Oracle Text enables you to perform sentiment analysis for a topic or document by using sentiment classifiers that are trained to identify sentiment metadata.

With growing amounts of data, organizations must gain more insights about their data rather than just obtaining hits in response to a search query. The insight could be in the form of answering certain basic types of queries (such as weather queries or queries about recent events) or providing opinions about user-specified topics. Keyword searches provide a list of results containing the search term. However, to identify a sentiment or opinion about the search term, must browse through the results and then manually locate the required sentiment information. Sentiment analysis provides a one-step process to identify sentiment information within a set of documents.

Sentiment analysis is the process of identifying and extracting sentiment metadata about a specified topic or entity from a set of documents. Trained sentiment classifiers identify the sentiment. When you run a query with sentiment analysis, in addition to the search results, sentiment metadata is also identified and displayed. Sentiment analysis provides answers to questions such as “Is a product review positive or negative?” or “Is the customer satisfied or dissatisfied?” For example, from a document set consisting of multiple reviews for a particular product, you can determine an overall sentiment that indicates if the product is good or bad.

#### 16.1.2 About Sentiment Classifiers

A sentiment classifier is a type of document classifier that is used to extract sentiment metadata about a topic or document.

To perform sentiment analysis by using a sentiment classifier, you must first associate a sentiment classifier preference with the sentiment classifier and then train the sentiment classifier.

You can associate user-defined sentiment classifiers with a sentiment classifier preference of type `SENTIMENT_CLASSIFIER.` A sentiment classifier preference specifies the parameters that are used to train a sentiment classifier. These parameters are defined as attributes of the sentiment classifier preference. You can either create a sentiment classifier preference or use the default `CTXSYS.DEFAULT_SENTIMENT_CLASSIFIER.` To create a user-defined sentiment classifier preference, use the `CTX_DDL.CREATE_PREFERENCE` procedure to define a sentiment classifier preference and the `CTX_DDL.SET_ATTRIBUTE` procedure to define its parameters.

To train a sentiment classifier, you need to provide an associated sentiment classifier preference, a training set of documents, and the sentiment categories. If you do not specify a classifier preference, then Oracle Text uses default values for the training parameters. You train the sentiment classifier by using the set of sample documents and the specified preference. You assign each sample document to a category. Oracle Text uses this sentiment classifier to deduce a set of classification rules that define how sentiment analysis must be performed. Use the `CTX_CLS.SA_TRAIN` procedure to train a sentiment classifier.

Typically, you define and train separate sentiment classifiers for different categories of documents, such as finance, product reviews, and music. If you do not want to create your own sentiment classifier or if suitable training data is not available to train your classifier, you can use the default sentiment classifier provided by Oracle Text. The default sentiment classifier is unsupervised.

**Note:**

The default sentiment classifier works only with `AUTO_LEXER.` Do not use `AUTO_LEXER` with user-defined sentiment classifiers.

**See Also:**

- Creating a Sentiment Classifier Preference

- Training Sentiment Classifiers

#### 16.1.3 About Performing Sentiment Analysis

To perform sentiment analysis, you run a sentiment query that includes the sentiment classifier which must be used to identify sentiment information. The classifier can be the default or a user-defined sentiment classifier.

You can perform sentiment analysis only as part of a search operation. Oracle Text searches for the specified keywords and generates a result set. Then, sentiment analysis is performed on the result set to identify a sentiment score for each result. If you do not explicitly specify a sentiment classifier in your query, the default classifier is used.

You can either identify one single sentiment for the entire document or separate sentiments for each topic within a document. Most often, a document contains multiple topics and the author’s sentiment toward each topic may be different. In such cases, document-level sentiment scores may not be useful because they cannot identify sentiment scores associated with different topics in the document. Identifying topic-level sentiment scores provides the required answers. For example, when searching through a set of documents containing reviews for a camera, a document-level sentiment tells you whether the camera is good or not. Assume that you want the general opinion about the picture quality of a camera. Performing a topic-level sentiment analysis, with “picture quality” as one of the topics provides the required information.

**Note:**

If you do not specify a topic of interest for sentiment analysis, then Oracle Text returns the overall sentiment for the entire document.

**See Also:**

- Performing Sentiment Analysis with the CTX_DOC Package

- Performing Sentiment Analysis with the RSI

#### 16.1.4 Sentiment Analysis Interfaces

Oracle Text supports multiple interfaces for performing sentiment analysis.

Use one of the following interfaces to run a sentiment query:

- Procedures in the `CTX_DOC` package

- XML Query Result Set Interface (RSI)

**See Also:**

- Performing Sentiment Analysis with the CTX_DOC Package

- Performing Sentiment Analysis with the RSI

### 16.2 Creating a Sentiment Classifier Preference

Use the `CTX_DDL.CREATE_PREFERENCE` procedure to create a sentiment classifier preference and the `CTX_DDL.SET_ATTRIBUTE` procedure to define its attributes. The classifier type associated with a user-defined sentiment classifier preference is `SENTIMENT_CLASSIFIER`.

To create a sentiment classifier preference:

1.  To define a sentiment classifier preference, use the `CTX_DDL.CREATE_PREFERENCE` procedure. The classifier must be of type `SENTIMENT_CLASSIFIER.`
2.  To define attributes for the sentiment classifier preference, use the `CTX_DDL.SET_ATTRIBUTE` procedure. The attributes define the parameters that are used to train the sentiment classifier.

Example 16-1 Creating a Sentiment Classifier Preference

The following example creates a sentiment classifier preference named `clsfier_camera.` This preference is used to classify a set of documents that contain reviews for SLR cameras.

1.  Define a sentiment classifier preference named `clsfier_camera` with type `SENTIMENT_CLASSIFIER.`

        exec ctx_ddl.create_preference('clsfier_camera','SENTIMENT_CLASSIFIER');

2.  Define the attributes of the `clsfier_camera` sentiment classifier preference. Set 1000 for the maximum number of features to be extracted. Set 600 for the number of iterations for which the classifier runs.

        exec ctx_ddl.set_attribute('clsfier_camera','MAX_FEATURES','1000');
        exec ctx_ddl.set_attribute('clsfier_camera','NUM_ITERATIONS','600');

For attributes that are not explicitly defined, the default values are used.

**See Also:**

- [Oracle Text Reference](../ccref/CTX_DDL-package.md)

- About Sentiment Classifiers

### 16.3 Training Sentiment Classifiers

Training a sentiment classifier generates the classification rules that are used to provide a positive or negative sentiment for a search keyword.

The following example trains a sentiment classifier that can perform sentiment analysis on user reviews of cameras:

1.  Create and populate the training document table. This table contains the actual text of the training set documents or the file names (if the documents are present externally).
    Ensure that the training documents are randomly selected to avoid any possible bias in the trained sentiment classifier. The distribution of positive and negative documents must not be skewed. Oracle Text checks for the distribution while training the sentiment classifier.

        create table training_camera (review_id number primary key, text varchar2(2000));
        insert into training_camera values( 1,'/sa/reviews/cameras/review1.txt');
        insert into training_camera values( 2,'/sa/reviews/cameras/review2.txt');
        insert into training_camera values( 3,'/sa/reviews/cameras/review3.txt');
        insert into training_camera values( 4,'/sa/reviews/cameras/review4.txt');
2.  Create and populate the category table.
    This table specifies training labels for the documents present in the document table. It tells the classifier the true sentiment of the training set documents.

    The primary key of the document table must have a foreign key relationship with the unique key of the category table. The names of these columns must be passed to the `CTX_CLS.SA_TRAIN` procedure so that the sentiment label can be associated with the corresponding document.

    Oracle Text validates the parameters specified for the classifier preference and the `category` values. The `category` values are restricted to 1 for positive, 2 for negative, and 0 for neutral sentiment. Documents with a `category` of 0 (neutral documents) are not used while training the classifier. Additional columns in the category table, other than document ID and category, are also not used by the classifier.

        create table train_category (doc_id number, category number, category_desc varchar2(100));

        insert into train_category values (1,0,'neutral');
        insert into train_category values (2,1,'positive');
        insert into train_category values (3,2,'negative');
        insert into train_category values (4,2,'negative');
3.  Create the context index on the training document table. This index is used to extract metadata for training documents while training the sentiment classifier.
    In this example, create an index without populating it.

        exec ctx_ddl.create_preference('fds','DIRECTORY_DATASTORE');
        create index docx on training_camera(text) indextype is ctxsys.context parameters ('datastore fds nopopulate');
4.  (Optional) Create a `clsfier_camera` sentiment classifier preference that performs sentiment analysis on a document set consisting of camera reviews.
5.  Train the sentiment classifier `clsfier_camera.`
    During training, Oracle Text determines the ratio of positive to negative documents. If this ratio is not in the range of 0.4 to 0.6, then a warning written to the CTX log indicates that the sentiment classifier is skewed. After the sentiment classifier is trained, it is ready to be used in sentiment queries to perform sentiment analysis.

    In the following example, `clsfier_camera` is the name of the sentiment classifier that is being trained, `review_id` is the name of the document ID column in the document training set, `train_category` is the name of the category table that contains the labels for the training set documents, `doc_id` is the document ID column in the category table, `category` is the category column in the category table, and `clsfier` is the name of the sentiment classifier preference that is used to train the classifier.

        exec ctx_cls.sa_train_model('clsfier_camera','docx','review_id','train_category','doc_id','category','clsfier');

    **Note:**

    If you do not specify a sentiment classifier preference when running the `CTX_CLS.SA_TRAIN_MODEL` procedure, then Oracle Text uses the default preference `CTXSYS.DEFAULT_SENTIMENT_CLASSIFIER.`

**Related Topics**

- About Sentiment Classifiers
- Creating a Sentiment Classifier Preference
- [Oracle Text Reference](../ccref/CTX_CLS-package.md)

### 16.4 Performing Sentiment Analysis with the CTX_DOC Package

Use the procedures in the `CTX_DOC` package to perform sentiment analysis on a single document within a document set. For each document, you can either determine a single sentiment score for the entire document or individual sentiment scores for each topic within the document.

Before you perform sentiment analysis, you must create a context index on the document set. The following command creates a `camera_revidx` context index on the document set in the `camera_reviews` table:

    create index camera_revidx on camera_reviews(review_text) indextype is
    ctxsys.context parameters ('lexer mylexer stoplist ctxsys.default_stoplist');

To perform sentiment analysis with the `CTX_DOC` package, use one of the following methods:

- Run the `CTX_DOC.SENTIMENT_AGGREGATE` procedure with the required parameters.
  This procedure provides a single consolidated sentiment score for the entire document.

  The sentiment score is a value in the range of -100 to 100, and it indicates the strength of the sentiment. A negative score represents a negative sentiment and a positive score represents a positive sentiment. Based on the sentiment scores, you can group scores into labels such as Strongly Negative (–80 to –100), Negative (–80 to –50), Neutral (-50 to +50), Positive (+50 to +80), and Strongly Positive (+80 to +100).
- Run the `CTX_DOC.SENTIMENT` procedure with the required parameters.
  This procedure returns the individual segments within the document that contain the search term, and provides an associated sentiment score for each segment.

Example 16-2 Obtaining a Single Sentiment Score for a Document

The following example uses the `clsfier_camera` sentiment classifier to provide a single aggregate sentiment score for the entire document. The sentiment classifier was created and trained. The table containing the document set has a `camera_revidx` context index. The `doc_id` of the document within the document table for which sentiment analysis must be performed is 49. The topic for which a sentiment score is being generated is ‘Nikon.’

    select ctx_doc.sentiment_aggregate('camera_revidx','49','Nikon','clsfier_camera') from dual;

    CTX_DOC.SENTIMENT_AGGREGATE('CAMERA_REVIDX','49','NIKON','CLSFIER_CAMERA')
    --------------------------------------------------------------------------
                                74
    1 row selected.

Example 16-3 Obtaining a Single Sentiment Score with the Default Classifier

The following example uses the default sentiment classifier to provide an aggregate sentiment score for the entire document. The table containing the document set has a `camera_revidx` context index. The `doc_id` of the document within the document table for which sentiment analysis must be performed is 1.

    select ctx_doc.sentiment_aggregate('camera_revidx','1') from dual;

    CTX_DOC.SENTIMENT_AGGREGATE('CAMERA_REVIDX','1')
    --------------------------------------------
                                               2

    1 row selected.

Example 16-4 Obtaining Sentiment Scores for Each Topic Within a Document

The following example uses the `clsfier_camera` sentiment classifier to generate sentiment scores for each segment within the document. The sentiment classifier was created and trained. The table containing the document set has a `camera_revidx` context index . The `doc_id` of the document within the document table for which sentiment analysis must be performed is 49. The topic for which a sentiment score is being generated is ‘Nikon.’ The `restab` result table, which will be populated with the analysis results, was created with the columns snippet (`CLOB`) and score (`NUMBER`).

    exec ctx_doc.sentiment('camera_revidx','49','Nikon','restab','clsfier_camera', starttag=>'<<', endtag=>'>>');

    SQL> select * from restab;
    SNIPPET
    --------------------------------------------------------------------------------
         SCORE
    ----------
    It took <<Nikon>> a while to produce a superb compact 85mm lens, but this time they finally got it right.
            65

    Without a doubt, this is a fine portrait lens for photographing head-and-shoulder portraits (The only lens which is optically better is
    <<Nikon>>'s legendary 10
    5mm f2.5 Nikkor lens, and its close optical twin, the 105mm f2.8 Micro Nikkor.
            75

    Since the 105mm f2.5 Nikkor lens doesn't have an autofocus version, then this might be the perfect moderate telephoto lens for owners of
    <<Nikon>> autofocus
    SLR cameras.
            84
    3 rows selected.

Example 16-5 Obtaining a Sentiment Score for a Topic Within a Document

The following example uses the `tdrbrtsent03_cl` sentiment classifier to generate a sentiment score for each segment within the document. The sentiment classifier was created and trained. The table containing the document set has a `tdrbrtsent03_idx` context index. The `doc_id` of the document within the document table for which sentiment analysis must be performed is 1. The topic for which a sentiment score is being generated is ‘movie.’ The `tdrbrtsent03_rtab` result table, which will be populated with the analysis results was created with the columns snippet and score.

    SQL> exec ctx_doc.sentiment('tdrbrtsent03_idx','1','movie','tdrbrtsent03_rtab','tdrbrtsent03_cl');
    PL/SQL procedure successfully completed.

    SQL> select * from tdrbrtsent03_rtab;
    SNIPPET
    --------------------------------------------------------------------------------      
    SCORE
    ----------
    the <b>movie</b> is a bit overlong , but nicholson is such good fun that the running time passes by pretty quickly
     -62

    1 row selected.

**See Also:**

- `CTX_DOC.SENTIMENT_AGGREGATE` in the [Oracle Text Reference](../ccref/CTX_DOC-package.md)

- `CTX_DOC.SENTIMENT` in the [Oracle Text Reference](../ccref/CTX_DOC-package.md)

### 16.5 Performing Sentiment Analysis with the RSI

The XML Query Result Set Interface (RSI) enables you to perform sentiment analysis on a set of documents by using either the default sentiment classifier or a user-defined sentiment classifier. The documents on which sentiment analysis must be performed are stored in a document table.

Use the `sentiment` element in the input RSI to indicate that sentiment analysis, in addition to other operations specified in the Result Set Descriptor (RSD), must be performed at query time. If you specify a value for the `classifier` attribute of the `sentiment` element, then the specified sentiment classifier is used to perform the sentiment analysis. If the `classifier` attribute is omitted, then Oracle Text performs sentiment analysis by using the default sentiment classifier. The `sentiment` element contains a child element called `item` that specifies the topic or concept about which a sentiment must be generated during sentiment analysis.

You can generate either a single sentiment score for each document or separate sentiment scores for each topic within the document. Use the `agg` attribute of the `item` element to generate a single aggregated sentiment score for each document.

You can perform sentiment classification by using a keyword query or the `ABOUT` operator. When you use the `ABOUT` operator, the result set includes synonyms of the keyword that are identified by using the thesaurus.

To perform sentiment analysis by using RSI:

1.  Create and train the sentiment classifier you will use to perform sentiment analysis.
2.  Create the document table that contains the documents to be analyzed and a context index on the document table.
3.  Use the required elements and attributes within a query to perform sentiment analysis.
    The RSI must contain the `sentiment` element.

Example 16-6 Input the RSD to Perform Sentiment Analysis

The following example performs sentiment analysis and generates a sentiment for the ‘lens’ topic. The driving query is a keyword query for ‘camera.’ The `sentiment` element specifies that sentiment analysis must be performed by using the `clsfier_camera` sentiment classifier. This classifier was previously created and trained by using the `CTX_CLS.SA_TRAIN_MODEL` procedure. The `camera_revidx` context index is on the document set table.

The sentiment score ranges from -100 to 100. A positive score indicates positive sentiment, whereas a negative score indicates negative sentiment. The absolute value of the score is indicative of the magnitude of positive and negative sentiment.

To perform sentiment analysis and obtain a sentiment score for each topic within the document:

1.  Create the `rs` result set table that will store the results of the search operation.

        SQL> var rs clob;
        SQL> exec dbms_lob.createtemporary(:rs, TRUE, DBMS_LOB.SESSION);

2.  Perform sentiment analysis as part of a search query.

    The keyword being searched for is ‘camera.’ The topic for which sentiment analysis is performed is ‘lens.’

        begin
        ctx_query.result_set('camera_revidx','camera','
            <ctx_result_set_descriptor>
                <hitlist start_hit_num="1" end_hit_num="10" order="score desc">
                <sentiment classifier="clsfier_camera">
                   <item topic="lens" />
                   <item topic="picture quality" agg="true" />
               </sentiment> </hitlist>
           </ctx_result_set_descriptor>',:rs);
        end;
        /

3.  View the results stored in the result table.

    Other applications can use the XML result set for further processing. For brevity, some output was removed. For each segment within the document, a score represents the sentiment score for the segment.

        SQL> select xmltype(:rs) from dual;
        XMLTYPE(:RS)
        --------------------------------------------------------------------------------
        <ctx_result_set>
          <hitlist>
            <hit>
              <sentiment>
                 <item topic="lens">          
                    <segment>             
                       <segment_text>The first time it was sent in was because the <b>lens </b> door failed to turn on the camera
        and it was almost to come off of its track . Eight months later, the flash quit working in all modes AND the door was
        failing AGAIN!</segment_text>           
                        <segment_score>-81</segment_score>           
                   </segment>         
                </item>        
                 <item topic="picture quality"> <score> -75 </score>       
                 </item>
              </sentiment>
            </hit>
            <hit>
               <sentiment>
                  <item topic="lens">
                     <segment>
                         <segment_text>I was actually quite impressed with it. Powerful zoom , sharp <b>lens</b>, decent picture
        quality. I also played with some other Panasonic models in various stores just to get a better feel for them, as well as
        spent a few hours on </segment_text> 
                          <segment_score> 67 </segment_score>           
                    </segment>        
                  </item>         
                     <item topic="picture quality">  <score>-1</score>    </item>
               </sentiment>
            </hit>
            . . .
          . . .
          </hitlist>
        </ctx_result_set>

**See Also:**

[Oracle Text Reference](../ccref/CTX_QUERY-package.md)
