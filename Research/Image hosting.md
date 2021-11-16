# Image storing for web development

While developing websites you're probably gonna need images. How and where do you store these images and what are some best practices?

A couple of things to keep in mind while storing images is caching, (relatable) quality and different versions with different dimensions to name a few.

<br>

### Caching

Caching makes sure your webpage visitors don't have to download all your webpage's images every time they visit your website. Instead they will be saved inside the visitor's browser.

A problem that might occur with caching is not showing updated images, but instead the older cached ones. One way to solve this problem will be explained in this article:

> You can get your developer to automatically add the MD5 hash of all uploaded images to their URLs, as they are uploaded. The MD5 is essentially an image’s fingerprint. When an > image changes, so does the MD5 and thus the URL of the image, which means that each time you update your images, the browser is forced to grab the new image.

<i> Source: https://www.catchpoint.com/blog/image-upload-best-practices </i>

<br>

### Quality

It starts off with the right image formats, this piece of the article explains why it's better to use JPEG:

> The main thing to note is that you should never upload PNGs as photographs. There is typically no perceivable difference in quality between a JPEG photo and a PNG photo, but  > the latter format tends to result in images with huge file sizes that waste a lot of bandwidth. Only ever use PNGs for logos, charts, or when you need transparency.  

<i> Source: https://www.catchpoint.com/blog/image-upload-best-practices </i>

Reduce the quality from your images, high resolution images aren't neccessary most of the time. Reducing quality will result into smaller size which positively affects the user experience because of faster response time.

The last thing is compressing images which can sometimes be done without losing quality but reduces that file size.

<br>

### Different versions

If you keep multiple versions of the same image with different dimensions (e.g. 300px x 300px) you can serve your pages faster rather than letting software do it for you. Think about thumbnails aswell as the full image on a details page for example. 

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

> Use Content Delivery Networks

> Hosting images on the same server you use for your website is a terribly inefficient way to deliver images to your website’s visitors. Uploading all images to the same server > that’s used to run your website puts a huge strain on the server, which ends up slowing down your load times. The end result of slow load times on your site is reduced traffic > and thus lower sales.

> One of the best things you can do to manage your images is to upload them for hosting on a content delivery network (CDN). A CDN is essentially a globally distributed network > of servers. When someone browses your site, the CDN routes the user to the server nearest to their location, which dramatically improves the performance of your pages by      > speeding up the image delivery to the end user.  
> source: <cite>https://www.catchpoint.com/blog/image-upload-best-practices</cite>

## Inside the root folder with direct paths inside the pages

##


