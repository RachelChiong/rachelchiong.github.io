
{:refdef: style="text-align: center;"}
 ![Welcome banner](images/welcome-banner-1.gif)
{: refdef}

And you can include links, like this [link to fast.ai](https://www.fast.ai). Posts will appear after this file.

<h1>All posts</h1>
{% for post in site.posts %}
<div class="post-preview" style="display: flex; margin-bottom: 20px;">
 <img class="post-preview__left" src="{{ post.image }}" alt="{{ page.image_alt }}" style="max-height: 200px;">
 <div class="post-preview__right" style="margin-left: 10px; position: relative; width: 100%;">
   <a class="preview-title" href="{{ post.url }}">{{ post.title }}</a>
   <span>{{ post.date | date: "%b %d, %Y" }}</span>
   {{post.excerpt}}
   <div class="tag-group">
     {% for tag in post.tags %}
       <div class="tag"><span class="tag-text">{{ tag }}</span></div>
     {% endfor %}
   </div>
 </div>

</div>

{% endfor %}