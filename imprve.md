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



Search
========================================================================
Libraries and software for indexing and performing search queries on data.

django-haystack - Modular search for Django.
elasticsearch-py - The official low-level Python client for Elasticsearch.
solrpy - A Python client for solr.
Whoosh - A fast, pure Python search engine library.


email libraries
=========================================================Email

Libraries for sending and parsing email.

inbox.py - Python SMTP Server for Humans.
imbox - Python IMAP for Humans.
inbox - The open source email toolkit.
lamson - Pythonic SMTP Application Server.
flanker - A email address and Mime parsing library.
marrow.mailer - High-performance extensible mail delivery framework.
django-celery-ses - Django email backend with AWS SES and Celery.
modoboa - A mail hosting and management platform including a modern and simplified Web UI.
envelopes - Mailing for human beings.
mailjet - Mailjet API implementation for batch mailing, statistics and more.
Talon - Mailgun library to extract message quotations and signatures.
pyzmail - Compose, send and parse emails.


==================================
for other tool information follow bellow link
https://github.com/vinta/awesome-python#restful-api


about match button 
==================================
If you asked some question in home page like post.
EX: I am going to movie will you come?
	then some peoples give their feed back in commment.
	But We are providing Match Button By single click interested person is ready to come with you.
	
about Done , do tasks
==================================
If I am going to movie 		:Task Not completed
If some body went to movie	:Completed Task.

Based on completed , yet to complete actions we can find best matches.


