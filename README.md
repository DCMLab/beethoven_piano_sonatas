# annotation_workflow_template

This repo holds the current version of the DCML annotation workflow which is pulled by all subcorpus repos upon push to their main branch. 

Please note that the `meta_ corpora` branch should be used with collections of corpora.


# Overview
|file_name|measures|labels|standard|                    annotators                    |    reviewers     |
|---------|-------:|-----:|--------|--------------------------------------------------|------------------|
|01-1     |     152|   241|2.2.0   |Lars & Ya-Chuan (2.2.0), John Heilig (2.3.0)      |AN                |
|01-2     |      61|   204|2.2.0   |Lars & Ya-Chuan                                   |Adrian Nagel      |
|01-3     |      73|   132|2.3.0   |Daniel Grote (2.2.0), Adrian Nagel (2.3.0)        |Adrian Nagel      |
|01-4     |     196|   355|2.2.0   |Daniel Grote                                      |Adrian Nagel      |
|02-1     |     336|     0|        |                                                  |                  |
|02-2     |      80|     0|        |                                                  |                  |
|02-3     |      68|     0|        |                                                  |                  |
|02-4     |     187|     0|        |                                                  |                  |
|03-1     |     257|   487|2.3.0   |Lydia Carlisi (2.2.0), John Heilig (2.3.0)        |AN                |
|03-2     |      82|   233|2.2.0   |Lydia Carlisi                                     |                  |
|03-3     |     127|   198|2.3.0   |Lydia Carlisi (2.2.0), Adrian Nagel (2.3.0)       |                  |
|03-4     |     312|   794|2.2.0   |Lydia Carlisi                                     |                  |
|04-1     |     362|     0|        |                                                  |                  |
|04-2     |      90|     0|        |                                                  |                  |
|04-3     |     150|     0|        |                                                  |                  |
|04-4     |     186|     0|        |                                                  |                  |
|05-1     |     284|   310|2.3.0   |Adrian Nagel (2.2.0), Hanné Becker (2.3.0)        |AN                |
|05-2     |     112|   252|2.3.0   |Adrian Nagel (2.3.0)                              |                  |
|05-3     |     122|   314|2.2.0   |Adrian Nagel                                      |                  |
|06-1     |     202|   338|2.3.0   |Adrian Nagel (2.2.0), Amelia Brey (2.3.0)         |AB                |
|06-2     |     170|   236|2.3.0   |Gabriele Ortiz Würth (2.2.0), Adrian Nagel (2.3.0)|Johannes Hentschel|
|06-3     |     150|   309|2.2.0   |Adrian Nagel                                      |                  |
|07-1     |     344|   527|2.3.0   |Lydia Carlisi (2.2.0), Amelia Brey (2.3.0)        |AB                |
|07-2     |      87|   217|2.2.0   |Lydia Carlisi                                     |                  |
|07-3     |      86|    90|2.2.0   |Lydia Carlisi                                     |                  |
|07-4     |     113|   266|2.2.0   |Lydia Carlisi                                     |                  |
|08-1     |     310|   503|2.3.0   |Lydia Carlisi (2.2.0), John Heilig (2.3.0)        |AN                |
|08-2     |      73|   143|2.3.0   |Lydia Carlisi (2.2.0), Adrian Nagel (2.3.0)       |                  |
|08-3     |     210|   364|2.2.0   |Lydia Carlisi                                     |                  |
|09-1     |     161|   351|2.3.0   |Lydia Carlisi (2.2.0), Amelia Brey (2.3.0)        |AB, AN            |
|09-2     |     178|   231|2.2.0   |Lydia Carlisi                                     |                  |
|09-3     |     131|   262|2.2.0   |Lydia Carlisi                                     |                  |
|10-1     |     200|   355|2.3.0   |Daniel Grote (2.2.0), John Heilig (2.3.0)         |AN                |
|10-2     |      90|   353|2.2.0   |Daniel Grote                                      |                  |
|10-3     |     254|   339|2.2.0   |Adrian Nagel                                      |                  |
|11-1     |     199|     0|        |                                                  |                  |
|11-2     |      77|     0|        |                                                  |                  |
|11-3     |      46|     0|        |                                                  |                  |
|11-4     |     199|     0|        |                                                  |                  |
|12-1     |     219|     0|        |                                                  |                  |
|12-2     |      95|     0|        |                                                  |                  |
|12-3     |      75|     0|        |                                                  |                  |
|12-4     |     170|     0|        |                                                  |                  |
|13-1     |      88|     0|        |                                                  |                  |
|13-2     |     147|     0|        |                                                  |                  |
|13-3     |      26|     0|        |                                                  |                  |
|13-4     |     285|     0|        |                                                  |                  |
|14-1     |      69|     0|        |                                                  |                  |
|14-2     |      60|     0|        |                                                  |                  |
|14-3     |     201|     0|        |                                                  |                  |
|15-1     |     462|     0|        |                                                  |                  |
|15-2     |     103|     0|        |                                                  |                  |
|15-3     |      94|     0|        |                                                  |                  |
|15-4     |     210|     0|        |                                                  |                  |
|16-1     |     325|   303|2.3.0   |Adrian Nagel (2.2.0), Hanné Becker (2.3.0)        |AN                |
|16-2     |     119|   285|2.2.0   |Adrian Nagel                                      |                  |
|16-3     |     275|   703|2.2.0   |Adrian Nagel                                      |                  |
|17-1     |     228|   352|2.3.0   |Adrian Nagel (2.2.0), Hanné Becker (2.3.0)        |AN                |
|17-2     |     103|   223|2.3.0   |Adrian Nagel (2.3.0)                              |                  |
|17-3     |     399|   460|2.3.0   |Adrian Nagel (2.3.0)                              |                  |
|18-1     |     253|   269|2.3.0   |Adrian Nagel (2.2.0), Hanné Becker (2.3.0)        |AN                |
|18-2     |     169|   273|2.3.0   |Adrian Nagel (2.3.0)                              |                  |
|18-3     |      61|   178|2.2.0   |Adrian Nagel                                      |                  |
|18-4     |     333|   455|2.2.0   |Adrian Nagel                                      |                  |
|19-1     |     110|   193|2.3.0   |Daniel Grote (2.2.0), Hanné Becker (2.3.0)        |AN (2.2.0 + 2.3.0)|
|19-2     |     164|   385|2.2.0   |Daniel Grote                                      |Adrian Nagel      |
|20-1     |     122|   286|2.3.0   |Lydia Carlisi (2.2.0), John Heilig (2.3.0)        |AN                |
|20-2     |     120|   168|2.2.0   |Lydia Carlisi                                     |                  |
|21-1     |     302|   616|2.3.0   |Adrian Nagel (2.2.0), Amelia Brey (2.3.0)         |AB, AN            |
|21-2     |      28|    82|2.2.0   |Adrian Nagel                                      |                  |
|21-3     |     543|   739|2.2.0   |Adrian Nagel                                      |                  |
|23-1     |     262|   434|2.3.0   |Daniel Grote (2.2.0), Hanné Becker (2.3.0)        |AN                |
|23-2     |      97|   220|2.2.0   |Daniel Grote                                      |                  |
|23-3     |     361|   396|2.2.0   |Daniel Grote                                      |                  |
|24-1     |     105|   286|2.3.0   |Adrian Nagel (2.2.0), Hanné Becker (2.3.0)        |AN                |
|24-2     |     183|   317|2.3.0   |Adrian Nagel (2.3.0)                              |                  |
|26-1     |     255|   537|2.3.0   |Adrian Nagel (2.2.0), John Heilig (2.3.0)         |AN                |
|26-2     |      42|   127|2.2.0   |Adrian Nagel                                      |                  |
|26-3     |     196|   317|2.3.0   |Adrian Nagel (2.3.0)                              |                  |
|30-1     |      99|   252|2.3.0   |Adrian Nagel (2.2.0), Amelia Brey (2.3.0)         |AB, AN            |
|30-2     |     177|   320|2.3.0   |Adrian Nagel (2.3.0)                              |                  |
|30-3     |     203|   656|2.3.0   |Adrian Nagel (2.3.0)                              |                  |
|31-1     |     116|   339|2.3.0   |Adrian Nagel (2.2.0), John Heilig (2.3.0)         |AN                |
|31-2     |     158|   201|2.3.0   |Adrian Nagel, Victor Zheng (2.3.0)                |AN                |
|31-3     |     212|   662|2.2.0   |Adrian Nagel                                      |                  |
|32-1     |     157|   576|2.3.0   |Adrian Nagel (2.2.0), Amelia Brey (2.3.0)         |AB, AN            |
|32-2     |     177|   869|2.3.0   |Adrian Nagel, Victor Zheng (2.3.0)                |                  |
