## Competency Questions

TVC can be used for answering several questions related to values that change in time, according to some context.

In the following subsections, some of them are introduced together with their respective SPARQL queries. 

The prefixes that are used in all the SPARQL queries provided below are defined as follows:

        PREFIX : <http://www.sparontologies.net/example/>
        PREFIX tvc: <http://purl.org/spar/tvc/>
        PREFIX ti: <http://www.ontologydesignpatterns.org/cp/owl/timeinterval.owl#>

### CQ1

What value did a specific entity hold, within which context, and during what time interval?
        
        SELECT ?value ?context ?startDate ?endDate WHERE {
            :john-doe tvc:hasValue ?sit .
            ?sit tvc:withValue ?value ;
                 tvc:withinContext ?context ;
                 tvc:atTime ?interval .
            OPTIONAL { ?interval ti:hasIntervalStartDate ?startDate . }
            OPTIONAL { ?interval ti:hasIntervalEndDate ?endDate . }
        }

### CQ2

Which entities held a specific value within a given context?

        SELECT ?entity ?sit WHERE {
            ?entity tvc:hasValue ?sit .
            ?sit tvc:withValue :editor-in-chief ;
                tvc:withinContext :journal-of-semantics .
        }
