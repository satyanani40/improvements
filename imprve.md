for improve query performance you must add indexs to mongodb collection\n

about mongodb stopwords and stemming
===================================	

Mongodb can automatically performs stemming and stopwords
the following url can give full description 
==> https://blog.codecentric.de/en/2013/01/text-search-mongodb-stemming/ 

mongodb can automatically give scoring for each searching text using text opertor the example is shown bellow.	

Here we are inserting new document.	
	db.txt.insert( {txt: "I am your father, Luke"} )

after inserted searching will be performed.	
	db.txt.runCommand( "text", { search : "father" } )	

the following output will be display.	
db.txt.runCommand("text", {search: "father"} ) 
{
        "queryDebugString" : "father||||||",
        "language" : "english",
        "results" : [
                {
                        "score" : 0.75, 
                        "obj" : {
                                "_id" : ObjectId("50e820689068856d0ac6a801"),
                                "txt" : "I am your father, Luke"
                        }
                }
        ],
        "stats" : {
                "nscanned" : 1,
                "nscannedObjects" : 0,
                "n" : 1,
                "timeMicros" : 114
        },
        "ok" : 1
}

this is second example. here we are inserting three documents for calculating scoring among search.
	db.txt.insert({txt: "I'm still waiting"})
	db.txt.insert({txt: "I waited for hours"})
	db.txt.insert({txt: "He waits"})
	db.txt.runCommand("text", {search: "wait"})
	{
		    "queryDebugString" : "wait||||||",
		    "language" : "english",
		    "results" : [
		            {
		                    "score" : 1,
		                    "obj" : {
		                            "_id" : ObjectId("50e82dc9c95b73b63ec5f5aa"),
		                            "txt" : "He waits"
		                    }
		            },
		            {
		                    "score" : 0.75,
		                    "obj" : {
		                            "_id" : ObjectId("50e82db5c95b73b63ec5f5a9"),
		                            "txt" : "I waited for hours"
		                    }
		            },
		            {
		                    "score" : 0.6666666666666666,
		                    "obj" : {
		                            "_id" : ObjectId("50e82dabc95b73b63ec5f5a8"),
		                            "txt" : "I'm still waiting"
		                    }
		            }
		    ],
		    "stats" : {
		            "nscanned" : 3,
		            "nscannedObjects" : 0,
		            "n" : 3,
		            "timeMicros" : 148
		    },
		    "ok" : 1
	}

geolocation findout python libraries may be useful in futhure
==============================================================

Geolocation

Libraries for geocoding addresses and working with latitudes and longitudes.

GeoDjango - A world-class geographic web framework.
geopy - Python Geocoding Toolbox.
pygeoip - Pure Python GeoIP API.
GeoIP - Python API for MaxMind GeoIP Legacy Database.
geojson - Python bindings and utlities for GeoJSON.
django-countries - A Django app that provides country choices for use with forms, flag icons static files, and a country field for models.
