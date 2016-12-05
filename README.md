# Apache_Spark_Advanced_Programming_(Batch Processing)

<p>It was great fun to run advanced spark program for processing batch data with my favorite language - JAVA. The fundamental data structure of Spark - <a href="https://spark.apache.org/docs/2.0.2/api/java/org/apache/spark/api/java/JavaRDD.html" class="button">Resilient Distributed Datasets (RDD)</a> was basis of all data transformation. Table down below lists the key concepts focused.</p>

<table style="width:100%">
  <tr>
    <th>Advanced Programming Concepts</th>
  </tr>
  <tr>
    <td>Shared Variables - Accumulator & Broadcast Variable</td>
  </tr>
  <tr>
    <td>Sharing Resources Per-Partition Basis</td>
  </tr>
  <tr>
    <td>Piping RDD's to external program</td>
  </tr>
  <tr>
    <td>Numeric RDD Operations using StatsCounter</td>
  </tr>
</table>

Project Background/Requirements:
--------------------------------
*   **Shared Variables - Accumulators:**
<p>Data consists of call signs received in a file (sample:-/src/main/resources/callsigns).</p>
<html>
<body>
<img src="https://github.com/PandeySudeep/Apache_Spark_Advanced_Programming_-Batch-Processing-/blob/master/callsigns.PNG" alt="call signs" style="width:304px;height:228px;">
</body>
</html>
<p>Use Accumulator variables to (i) count the occurence of a particular call sign, (ii) check validity of call signs, (iii) count number of blank lines in the file.</p>

*   **Shared Variables - Broadcast:**
<p>File (/src/main/resources/callsign_tbl_sorted) is available.</p>
<html>
<body>
<img src="https://github.com/PandeySudeep/Apache_Spark_Advanced_Programming_-Batch-Processing-/blob/master/callsign_tbl_sorted.PNG" alt="lookup table" style="width:304px;height:228px;">
</body>
</html>
<p>From file above, create a broadcast variable that holds an Array consisting of unique pairs - sign,country. Use this broadcast variable to look up country/countries for all signs.</p>

*   **Sharing Resources Per-Partition Basis:**
<p>Working with data on a per-partition basis allows us to avoid redoing setup work for each data element of the RDD. Operations like opening a database connection or creating a random-number generator are examples of setup steps that we wish to avoid doing for each element.Spark has <b><u>per-partition</u></b> versions of <b><i>map</i></b> and <b><i>foreach</i></b> to help reduce the cost of these operations by letting us run code only once for each partition of an RDD.<br><br>Share a connection pool <i><u>(using HttpClient, ContentExchange, ObjectMapper)</u></i> to web data to reuse for all elements in a partition. Use <b><i>mapPartitionsToPair()</i></b> which gives iterator of all elements of partition and expects us to return iterable object of our result.<br><br>Sample web data can be retrieved by calling http://new73s.herokuapp.com/qsos/KK6JKQ.json as seen below.</p>
<html>
<body>
<img src="https://github.com/PandeySudeep/Apache_Spark_Advanced_Programming_-Batch-Processing-/blob/master/webdata_call.PNG" alt="web log" style="width:304px;height:228px;">
</body>
</html>
<p>For each valid sign, fetch JSON objects with various fields and corresponding values.</p>

*   **Piping RDD to external program:**
<p>An external R program is available to compute single value from each element of RDD.</p>
<html>
<body>
<img src="https://github.com/PandeySudeep/Apache_Spark_Advanced_Programming_-Batch-Processing-/blob/master/external_R_program.PNG" alt="R script" style="width:304px;height:228px;">
</body>
</html>
<p>Pipe source RDD to the external program to retrieve new RDD of the computed values.</p>

*   **Numeric RDD Operations using StatsCounter:**
<p>Create <b>StatsCounter</b> object using <b>stats()</b> method. Use methods availabe in StatsCounter class like count(), mean(), sum(), max(), min(), variance(), sampleVariance(), stdev(), sampleStdev() to compute numeric metrics.</p>



