# PHP5 Wiki Parser

The aims of PHP5 Wiki Parser are: 
*   Parse [PMWIKI Syntax][1].
*   Parse MediWiki Syntax.
*   Easy to add or remove Syntax.

Index: 

1.  [Setup & Configuration][2]
2.  [Usage][3]
3.  [Design Overview][4]

<a name="1">
## Setup & Configuration
</a>

One of the main objectives of this project is not only to create a compatible parser but also to create a framework to allow any WIKI based syntax parsing. [Find out more...][4] 

I'll make the assumption that you have already downloaded the latest ZIP and extracted the contents.
Next steps are to setup the config.ini file, at the time of writing this I have not yet completed any "standard" configurations. If these exist they will be named after the supporting format i.e. the standard configuration for PMWIKI Syntax will be config.pmwiki.ini. Copy the version of the config file that supports the wiki syntax you want to use to config.ini. 

You should now find that the parser will operate as expected. Feel free to tweak the INI file to meet your requirements.

<a name="2">
##  Usage
</a> 

The wiki parser has only 2 functions. The __constructor() that takes no variables and prepares the object for the WIKI text, this function loads all the plugins into memory ready to be called as the Wiki text is parsed. The second function is the parsing function where the wiki text is passed and the HTML is returned.   
  
Below is an example (In the download "examples/test.php"): `
```
<?php
    require_once(dirname(__FILE__) . '/../wikiParser.class.php');
    $test = new wikiParser();
    echo ($test->parse(file_get_contents(dirname(__FILE__) . '/example.wiki')))
?>
```

<a name="3">
##  Design Overview
</a>

The WikiParser class provides the environment for the plugins to run in. It manages the text during the conversion splitting the files how the plugin expects, passing the text to each plugin based on the interfaces they implement. 

The configuration for the wiki parser is in the config.ini. This config file contains which plugins to run and which order to run them in. It then contains any configuration for the plugins themselves. For example you can configure the base URL for any internal wiki links (Shared across pmwiki and mediawiki plugins).

 [1]: http://www.pmwiki.org/wiki/PmWiki/MarkupMasterIndex
 [2]: #1
 [3]: #2
 [4]: #3
 [5]: #4
