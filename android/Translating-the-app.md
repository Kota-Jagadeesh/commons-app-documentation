# Translating the app

Thanks to the translation work of many volunteers this app is available in a multitude of languages.

Translation of the text content of the Wikimedia Commons Android app happens on the [Commons Android App project](https://translatewiki.net/w/i.php?title=Special:Translate&group=commons-android) on [translatewiki.net](https://translatewiki.net). 

## Getting an account on translatewiki

Getting a translator account on translatewiki is a bit cumbersome, but don't worry you will get one soon:

1. Create an account at https://translatewiki.net
2. To get "translate rights", first edit 20 [random keys](https://translatewiki.net/wiki/Special:TranslationStash?)
3. If for any reason that does not work, you can also ask in TranslateWiki's [chat](https://translatewiki.net/wiki/Special:WebChat).

## Terminology

Commons uses many elaborate terms. Before inventing your own translation for a term, please look at how this term is already translated in the Commons web interface or in the Commons help pages.

For instance, to translate "depicts", go to https://commons.wikimedia.org/wiki/Commons:Depicts and choose your language in the top banner (which says "_Other languages_"). If you can not find any translation, please do not hesitate to ask at the [Commons village pump](https://commons.wikimedia.org/wiki/Commons:Village_pump).

## How to add new languages
If your language is not available, please crate a new GitHub issue asking for it, and we will add it as soon as possible. Thanks!

# Internals

## How translations make their way into the app
The translations from the translatewiki project are [periodically committed directly to this project](https://github.com/commons-app/apps-android-commons/commits/master?author=translatewiki) by the translatewiki team and later released with the normal updates to the Play Store. This means that you just need to translate, and your translations will automatically be used by the app from the next [release](https://github.com/commons-app/apps-android-commons/releases). Only languages where more than 25% of the strings have been translated get exported.

Translatewiki is configured to export a certain list of languages to a certain file in this repo. 

This is defined in their [Git repository](https://phabricator.wikimedia.org/diffusion/GTWN/repository/master/) ([GitHub mirror](https://github.com/wikimedia/translatewiki/)) in [this yaml file](https://phabricator.wikimedia.org/diffusion/GTWN/browse/master/groups/Wikimedia/CommonsAndroid.yaml) ([copy at the GitHub mirror](https://github.com/wikimedia/translatewiki/blob/master/groups/Wikimedia/CommonsAndroid.yaml)). This file also describes what files contain the original strings in English, adding a new string to one of these files will automatically add it to the list of strings to translate.

## Developers: How to add a new string

You just need to add the new string to `app/src/main/res/values/strings.xml`.
It will automatically be sent for to the volunteers, and localized strings will be added to the `app/src/main/res/values-XYZ/strings.xml` files.
Similarly, to modify or remove strings, you just need to edit `app/src/main/res/values/strings.xml`.

## Fixing language mappings between TranslateWiki and Android

Once in a while, a newly translated language is not matched automatically to an Android locale. That makes the build fail with an error such as `values-ks-arab: Resource and asset merger: Invalid resource directory name`. When that happens, please submit to Gerrit (not GitHub) a change [like this one](https://gerrit.wikimedia.org/r/c/translatewiki/+/826587) to add a new line to [TEMPLATES>FILES>codeMap](https://phabricator.wikimedia.org/diffusion/GTWN/browse/master/groups/Wikimedia/CommonsAndroid.yaml$15).

## Statistics

[Here](https://translatewiki.net/w/i.php?title=Special%3AMessageGroupStats&x=D&group=commons-android&suppressempty=1) is the current rate of translations for each language.
