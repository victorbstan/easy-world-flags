easy-world-flags
================

Add world flags to your web project by a two letter country code, all html and css, no dependencies, simple.

## History

Inspired by https://github.com/kristianmandrup/world-flags, and in fact, all image assets and style-sheets were extracted from there.

I have found I needed to call up flags in an intuitive and programmable way, specifically, I was looking for a way to call up country flag images by their respective country codes. Which led me to extract this project from a more complex gem.

## Usage

1) Simply attach the .f16 class (or any of the other size options) to the wrapper of your target flag nodes.
2) Then add a tag that will become your flag node, either a `span`, `li`, `div`, or `i` will do. Add the `flag` class to this element, and the two letter country code name also as a class name.

Example:

```
<div class="f16">
	<i class="flag ca"></i>
</div>
```
## Country codes... are the key

You can get country codes from various utilities, for example, in Rails and Ruby there are gems which will readily assist you in extracting country codes from country names, IP numbers, Geo location information, etc. I leave it up to you how you get your country codes in there.

Here is a more complex example within a project which already has country codes available and is providing them as a ruby hash to the view:

Using the `gem 'countries'`, to extract the full country name from the provided country code. Image a hash of county codes and views as such: `{CA:402, US:50, GB:19, ...}`

```
<div class="f16">
	<% for cc in @country_codes %>
		<span class="tag">
			<i class="flag <%= cc[0].downcase %>"></i> <%= "#{Country.find_country_by_alpha2(cc[0]).name}: #{cc[1]}" %>
		</span>
	<% end %>
</div>
```
