---
layout: post
title:  "YouTube API の利用方法"
date:   2020-04-26 22:37:40 +0900
categories: jekyll update
---

利用方法について

{% highlight python %}

from apiclient.discovery import build


def search_from_youtube(api_key, query):
    youtube = build('youtube', 'v3', developerKey=api_key)
    
    search_response = youtube.search().list(
        part='snippet', q=query, order='viewCount', type='video'
    ).execute()
    
    return search_response


if __name__ == "__main__":

    api_key = ""
    query = "東海"

    response = search_from_youtube(api_key, query)
    print(response.keys())
    # => dict_keys(['kind', 'etag', 'nextPageToken', 'regionCode', 'pageInfo', 'items'])

    response_items = response["items"]
    for res_i in response_items:
        print(res_i)

{% endhighlight %}
