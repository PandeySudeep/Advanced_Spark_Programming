# Apache_Spark_Advanced_Programming_(Batch Processing)

It was great fun to run advanced spark program for processing batch data with my favorite language - JAVA. The fundamental data structure of Spark - <a href="https://spark.apache.org/docs/2.0.2/api/java/org/apache/spark/api/java/JavaRDD.html" class="button">Resilient Distributed Datasets (RDD)</a> was basis of all data transformation. Table down below lists the key concepts focused.

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
    <td>StatCounter Class</td>
  </tr>
</table>

Project Background/Requirements:
--------------------------------
*   **Data Transformation Pipeline:**
Data consists of call signs received in a file (sample:-/src/main/resources/callsigns).
<html>
<body>
<img src="https://github.com/PandeySudeep/Apache_Spark_Advanced_Programming_-Batch-Processing-/blob/master/callsigns.PNG" alt="call signs" style="width:304px;height:228px;">
</body>
</html>
<p>Use Accumulator variables to (i) count the occurence of a particular call sign, (ii) check validity of call signs, (iii) count number of blank lines in the file.</p>

