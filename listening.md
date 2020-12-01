---
layout: home
title: Listening
---

{% for post in site.posts limit: 15 %}
      {% unless post.draft %}
          {% if post.categories contains 'music' %}
                  <item>
                    {% if post.title != "" %}
                      <title>{{ post.title | xml_escape }}</title>
                    {% endif %}
                    <author>{{ site.email }} ({{ site.title }})</author>
                    <description>
                      {{ post.content | xml_escape }}
                    </description>
                    <pubDate>{{ post.date | date_to_rfc822 }}</pubDate>
                    <link>{{ post.url | absolute_url }}</link>
                    <guid isPermaLink="true">{{ post.url | absolute_url }}</guid>
                    {% for tag in post.tags %}
                    <category>{{ tag | xml_escape }}</category>
                    {% endfor %}
                    {% for cat in post.categories %}
                    <category>{{ cat | xml_escape }}</category>
                    {% endfor %}
                  </item>
          {% endif %}
      {% endunless %}
{% endfor %}