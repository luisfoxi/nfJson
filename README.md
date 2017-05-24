# nfJson 

**Provides a set of fast performance, reliable and easy to use Json functions using pure VFP.**

Project Manager: Marco Plaza

## Functions & Usage

( Each function is a single prg -  No additional dependencies / Requires VFP9 )

* oJson = **nfJsonRead(**cJsonString , _isFileName_,_lReviveCollections_**)**

* cJsonString = **nfJsonCreate(**oVfp, _lFormattedOutput, lNoNullArrayItems,cRootName,aMembersFlag_**)**

* **nfJsonToCursor(**cJson, _cCursorName ,  lForceImportFromArray_**)** ( creates cursor back from Json created using nfCursorToJson4vfp )

* **nfCursorToJson4vfp()**  _&& converts current open table/cursor to Json suitable for later use of nfJsonToCursor()_

* **nfCursorToJson(**_lReturnArray, lArrayofValues, lIncludestruct, lFormattedOutput_**)** __&&  converts current open table/cursor to Json 

* **nfCursorToObject(**_lCopyToArray, lIncludeStruct_**)**

## Tests & Sample files

*  **nfJsonPerfTest.prg:** just run it and choose one of the embedded json samples from the list to check performance on your pc. ( Allows you to parse Json from clipboard too. )

* **examples.prg**  will parse the next Json files included in  JsonSamples folder. just run from test folder and see sample code and output.

* **collectionTest.prg:** creates a complex collection , converts it to Json and back to vfp.

* Sample Json files included:
	* youtubesearch.json
	* cycloneForecast.json
	* dropbox.json
	* googleMapsDistance.json
	* iphone photo.json
	* mapquest.json
	* mySimpleArray.json
	* tweeter.json
	* weatherService.json
	* yahooweather.json

## Release Notes

2017/03/10  
* fixed: proper support for 19 character strings with ISO basic date format & different strictdate settings.

2017/02/05  
* fixed: nfJsonRead bug fix: incorrect parsing for strings terminated with escaped double quotes; minor changes & code refactoring.

2017/01/11  
* fixed: nfJsonRead: incorrect unescaped output with "set exact = on"
* escapetest.prg - removed "leftover" lines.

2017/01/11  
* fixed issue escaping values terminated with "
* nfJsonRead: removed parameter "isFile" now you can just pass a file name or string
* added test: escapeTest.prg

2016/09/28  
* minor bug fix: zero item collections created as 1 empty item collection 
* proper indent for raw/formatted collection objects

2016/08/16  
* nfJsonPerfTest: added compiled exe, samples file ships as a separate file for you to edit 
* fixed bug on test prgs: clean installs would fail due to missing temp folder on distribution zip w/o tests\temp folder 
* fixed bug on collectionTest

2016/07/22  
* nfJsonRead: Improved error management
* CollectionTest: added new test

2016/07/20  
* Fixed bug: missing closing curly brace on collections as object member
* Updated collections program test

2016/07/09  
* Automatic cast for datetime properties ( ISO-8601 basic format & vfp compilant as described on [https://en.wikipedia.org/wiki/ISO_8601#Times](https://en.wikipedia.org/wiki/ISO_8601#Times). )
* nfJsonToCursor Bug Fix: "Date/datetime evaluated to an invalid value" while running under "strictdate = 1" converting empty dates back from Json

2016/07/04  
* Added support for control characters encoding ( chr( 0) ~ chr(31) )

2016/05/05  
* invalid Json error shows calling program information

2016/04/02  
* complex nested objects/arrays validation
* missing object/array closures validation

2016/03/28  
* nfJsonRead performs JSON validation: invalid Json throws error indicating reason.
* nfJsonPerfTest: proper error management enabled for invalid Json input from clipboard
* nfJsonToCursor: use of strict date format