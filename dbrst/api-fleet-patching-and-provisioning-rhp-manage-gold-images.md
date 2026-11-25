Sort by

Task Path Method

Fleet Patching and Provisioning/RHP - Manage Gold Images

You can create gold images and series to manage your deployments.

[Add a new image series](op-series-seriesid-post.md)
Method: post

Path: `/series/{seriesId}`

[Add image to series](op-series-seriesid-images-imageid-post.md)
Method: post

Path: `/series/{seriesId}/images/{imageId}`

[Delete image series](op-series-seriesid-delete.md)
Method: delete

Path: `/series/{seriesId}`

[Deletes the specified image name](op-images-imageid-delete.md)
Method: delete

Path: `/images/{imageId}`

[Display the configuration of the specified image](op-images-imageid-get.md)
Method: get

Path: `/images/{imageId}`

[Get all the series](op-series-get.md)
Method: get

Path: `/series`

[Get image series](op-series-seriesid-get.md)
Method: get

Path: `/series/{seriesId}`

[Lists all the gold images](op-images-get.md)
Method: get

Path: `/images`

[Lists all the gold images that matches the specified query parameters.](op-images-search-get.md)
Method: get

Path: `/images/search`

[Remove image from series](op-series-seriesid-images-imageid-delete.md)
Method: delete

Path: `/series/{seriesId}/images/{imageId}`

[Schedules an import image operation](op-images-post.md)
Method: post

Path: `/images`

[Search series matching certain parameters](op-series-search-get.md)
Method: get

Path: `/series/search`

[Subscribe a user to a series](op-series-seriesid-users-userid-post.md)
Method: post

Path: `/series/{seriesId}/users/{userId}`

[Unsubscribe a user from a series](op-series-seriesid-users-userid-delete.md)
Method: delete

Path: `/series/{seriesId}/users/{userId}`
