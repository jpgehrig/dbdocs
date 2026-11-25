#

The diagram shows two rectangles, one on the top and one on the bottom, outlined in grey, labeled Datacenter 1 (top) and Datacenter 2 (bottom).

Datacenter1 contains a rectangle outlined in a dashed line labeled Shardgroup 1. Shardgroup 1 contains 3 shard icons labeled 1, 2, and 3.

Each of the shards contains 8 rows of data colored yellow, pink, or blue, to indicate that data on each shard in the same colors is replicated. Shard 1 has 4 rows colored yellow and 4 rows colored pink. A two headed arrow points to the 4 yellow rows on Shard 1 and on Shard 2 to indicate that the yellow data is replicated on those shards. A two headed arrow points to the pink rows on Shard 1 and Shard 3 to indicate that the pink data is replicated on those shards. There are also 4 blue rows on Shard 2 and Shard 3, and a two headed arrow points to those rows indicating that the blue data is replicated on those shards.

Datacenter 2 contains a rectangle outlined with a dashed line labeled Shardgroup 2. Shardgroup 2 conatins 2 shard icons labeld 4 and 5.

Shard 4 and Shard 5 each contain 4 rows of pink, yellow and blue data and there is a two headed arrow between the shards indicating that all of the data is replicated between the shards.

There are three dashed line arrows between Shardgroup 1 and Shardgroup 2, which reside in different data centers, indicating that the data is replicated between Shardgroup 1 and Shardgroup 2.
