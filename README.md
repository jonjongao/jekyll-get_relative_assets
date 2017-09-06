# jekyll-get_relative_assets

Use include trick to do repeatedly code (just like function) to fetching relative static assets.

## Introduction

This code block required 3 input:

`directory` Main directory is child of assets. e.g. img, css, js

`url` Page url for navigate to asset directory, You have to organize asset files like the way of Page permalink.

i.e. Project permalink: /projects/my-project/ => Asset hierarchy: ./assets/img/projects/my-project/

I navigate my directory by absolute path, but you can change code to just check `contains` if you don't need it.

`find` Filter to scope down specific asset: thumbnail, cover, image.

## Usage

First, **capture** the return

    {% capture all_asset_path %}
    {% include get_relative_assets directory='img' url=project.url find='thumbnail' %}
    {% endcapture %}

Then **strip** it and split as array, note: You must strip it first otherwise you get lot of line break and space, and I mean **A LOT**.

    {% assign all_asset_path = all_asset_path | strip_newlines | strip | split: '|' | sort %}
    
That's it!

## References
[Using Jekyll _includes as custom liquid functions](http://hamishwillee.github.io/2014/11/13/jekyll-includes-are-functions/)
