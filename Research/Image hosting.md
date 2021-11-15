# Ways to store images for web development


## Directly inside in a database

BLOB column

### Reasons to store or not to store images in a database

> I'm in charge of some applications that manage many TB of images. We've found that storing file paths in the database to be best.
> 
> There are a couple of issues:
> 
> * database storage is usually more expensive than file system storage
> * you can super-accelerate file system access with standard off the shelf products
>     * for example, many web servers use the operating system's sendfile() system call to asynchronously send a file directly from the file system to the network interface. Images stored in a database don't benefit from this optimization.
> * things like web servers, etc, need no special coding or processing to access images in the file system
> * databases win out where transactional integrity between the image and metadata are important.
>     * it is more complex to manage integrity between db metadata and file system data
>     * it is difficult (within the context of a web application) to guarantee data has been flushed to disk on the filesystem
>     
> source: <cite>https://stackoverflow.com/questions/3748/storing-images-in-db-yea-or-nay</cite>



> As with most issues, it's not as simple as it sounds. There are cases where it would make sense to store the images in the database.
> 
> * You are storing images that are changing dynamically, say invoices and you wanted to get an invoice as it was on 1 Jan 2007?
> * The government wants you to maintain 6 years of history
> * Images stored in the database do not require a different backup strategy. Images stored on filesystem do
> * It is easier to control access to the images if they are in a database. Idle admins can access any folder on disk. It takes a really determined admin to go snooping in a database to extract the images
> 
> On the other hand there are problems associated
> * Require additional code to extract and stream the images
> * Latency may be slower than direct file access
> * Heavier load on the database server
> 
> source: <cite>https://stackoverflow.com/questions/3748/storing-images-in-db-yea-or-nay</cite>



## Inside a file storage system with the paths inside the database

Cloudinary
Amazon S3

## Inside the root folder with direct paths inside the pages

##




https://www.catchpoint.com/blog/image-upload-best-practices
https://www.reddit.com/r/webdev/comments/3iy1z1/how_should_i_store_useruploaded_images_for_a_web/
https://stackoverflow.com/questions/17121851/how-should-i-store-the-images-for-my-website
https://www.researchgate.net/post/How_to_store_images_photos_in_database_in_mysql
