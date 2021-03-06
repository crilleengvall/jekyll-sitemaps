![Jekyll sitemaps](https://www.christianengvall.se/wp-content/uploads/2017/01/jekyll-sitemaps.png "Jekyll sitemaps logo")

# jekyll-sitemaps
Generates sitemap for pages, posts, archives/categories, collections and images.    
Live example: [https://www.christianengvall.se/sitemap.xml](https://www.christianengvall.se/sitemap.xml "Live example")

## Installation
1. [Download](https://github.com/crilleengvall/jekyll-sitemaps/archive/master.zip "Download jekyll sitemaps") Jekyll sitemaps.
2. Copy `category-sitemap.xml`, `page-sitemap.xml`, `post-sitemap.xml`, `project-sitemap.xml` and `sitemap.xml` to your root folder.
3. Copy `_includes/single-post-sitemap.html` to your `_includes` folder.
4. Edit images in `single-post-sitemap.xml` as described under Images below.
5. If you do not use jekyll-archives plugin disable that as described under Categories below.
6. Edit or remove collections sitemap as described under Collections below.

## Images
[Google supports adding images](https://support.google.com/webmasters/answer/178636?hl=en "Sitemap images") to the sitemap. You need to edit the image url of your post(if any) on line 5 in `single-post-sitemap.html`.    
If you do not use images you can remove lines 4 to 8.
```
  <image:image>
    <image:loc>{{ post.image.source | absolute_url }}</image:loc>
    <image:title><![CDATA[{{ post.title }}]]></image:title>
    <image:caption><![CDATA[{{ post.title }}]]></image:caption>
  </image:image>
```
## Categories
This plugin supports jekyll-archives. This sitemap is created with the category-sitemap.xml file. If you do not use the jekyll archives plugin you should delete category-sitemap.xml and remove the following from sitemap.xml:
```
	<sitemap>
		<loc>{{ site.url }}/category-sitemap.xml</loc>
		<lastmod>{{ site.time | date_to_xmlschema }}</lastmod>
	</sitemap>
```

## Collections
Since collections are dynamic only an example is added with jekyll-sitemaps.
If you do not use collections you can delete project-sitemap.xml and the following from sitemap.xml:
```
	<sitemap>
		<loc>{{ site.url }}/project-sitemap.xml</loc>
		<lastmod>{{ site.time | date_to_xmlschema }}</lastmod>
	</sitemap>
```

If you do use collections you need to change this:    
    
1. Change `site.projects` to `site.<name-of-collection>` in project-sitemap.xml    
2. Change filename of `project-sitemap.xml` to `<name-of-collection>-sitemap.xml`    
3. Change the reference from `project-sitemap.xml` to `<name-of-collection>-sitemap.xml` in sitemap.xml:    
```
	<sitemap>
		<loc>{{ site.url }}/<name-of-collection>-sitemap.xml</loc>
		<lastmod>{{ site.time | date_to_xmlschema }}</lastmod>
	</sitemap>
```
