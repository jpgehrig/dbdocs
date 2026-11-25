# Description of the illustration ccapp011.eps

This illustration depicts the Oracle Text indexing process. The process is described in the text; following is a description of the illustration.

On the far left, documents from three different sources (the Internet, an O/S file system, and a database) stream into datastore. These are then passed into a Filter, where they emerge as marked-up text. The marked-up text then goes to the Sectioner.

From the Sectioner, two paths emerge: the documents go to the Lexer, where they are converted to tokens, and then they are sent to the Indexing Engine. Meanwhile, the markup information leaves the Sectioner and goes directly to the Indexing Engine.

From the Indexing Engine, one arrow goes down to the database with an Oracle Text index. Another arrow, a two-way arrow, goes between the Indexing Engine and a Wordlist, while a second two-way arrow goes between the Indexing Engine and a Stoplist.
