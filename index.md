 ![Welcome banner](images/wecome-banner-1.gif)


And you can include links, like this [link to fast.ai](https://www.fast.ai). Posts will appear after this file.

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
    </li>
  {% endfor %}
</ul>