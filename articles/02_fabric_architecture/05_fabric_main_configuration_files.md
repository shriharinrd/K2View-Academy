# Fabric- Main Configuration Files

## Configuration Directory

Fabric configuration files are located under the following directory:  $K2_HOME/config. This directory contains the main configuration files for Fabric server. The **template** of Fabric configuration files is located under $K2_HOME/fabric/config.template. Note that you need to edit the configuration files under **$K2_HOME/config** and not under the template directory.

## Main Configuration Files

<table>
<tbody>
<tr>
<td width="300pxl">
<p><strong>Configuration File</strong></p>
</td>
<td width="600pxl">
<p><strong>Description</strong></p>
</td>
</tr>
<tr>
<td width="300">
<p><a href="/articles/02_fabric_architecture/05_fabric_main_configuration_files.md#configini">config.ini</a></p>
<p>&nbsp;</p>
</td>
<td width="600">
<p>This is the main configuration file of Fabric. It contains different sections of parameters and each section has its own parameter. Fabric default values are set for the commented parameters.</p>
</td>
</tr>
<tr>
<td width="300">
<p>iifConfig.ini</p>
</td>
<td width="600">
<p>The main configuration file of the IIDFinder mechanism.</p>
</td>
</tr>
<tr>
<td width="300">
<p><a href="/articles/02_fabric_architecture/05_fabric_main_configuration_files.md#configini">node.id</a></p>
</td>
<td width="600">
<p>This file lists the Fabric node identifiers for the Affinity mechanism and the support of several Fabric clusters on one Cassandra cluster.</p>
</td>
</tr>
<tr>
<td width="300">
<p>logback.xml</p>
</td>
<td width="600">
<p>Fabric log configuration file.</p>
</td>
</tr>
</tbody>
</table>

### config.ini

This is the main configuration file of Fabric. It contains different sections of parameters and each section has it own parameter. Fabric default value for commented parameters.

<table width="900pxl">
<tbody>
<tr>
<td width="170pxl">
<p><strong>Parameters Category</strong></p>
</td>
<td width="180pxl">
<p><strong>Section Names</strong></p>
</td>
<td width="550pxl">
<p><strong>Main Parameters</strong></p>
</td>
</tr>
<tr>
<td width="150pxl">
<p>Cassandra connection</p>
</td>
<td width="150pxl">
<ul>
<li>cassandra</li>
<li>default_session</li>
</ul>
</td>
<td width="550pxl">
<p>The configuration required to create a connection to the Cassandra cluster:</p>
<ul>
<li>Replication options</li>
<li>Consistency level</li>
<li>Cassandra's connection details.</li>
<li>Set an SSL connection.</li>
</ul>
</td>
</tr>
<tr>
<td width="150pxl">
<p>Fabric Settings</p>
</td>
<td width="150pxl">
<ul>
<li>fabric</li>
<li>fabric_cluster</li>
<li>jdbc-server</li>
</ul>
</td>
<td width="550pxl">
<ul>
<li>Date and time formats.</li>
<li>Storage and Export directories</li>
<li>Fabric auditing settings</li>
<li>Connection pools settings</li>
<li>A maximum number of concurrent connections that are allowed for a single data source.</li>
<li>Batch process settings</li>
<li>Default <a href="/articles/14_sync_LU_instance/02_sync_modes.md">Sync mode</a></li>
<li>Sync of Common (reference) tables</li>
<li>Parallel Sync on <a href="/articles/07_table_population/13_LU_table_population_execution_order.md#how-do-i-set-the-population-order">Table Populations with the same execution order</a>.</li>
<li>Enable running <a href="/articles/02_fabric_architecture/04_fabric_commands.md#delete-instances-if-not-exist">DELETE INSTANCES IF NOT EXIST</a> Fabric command.</li>
<li>LUI compression types when storing the LUI in Cassandra.</li>
<li>Web service parameters</li>
<li>Fabric interaction with Cassandra for user&rsquo;s removal, addition, of edit activities.</li>
<li>Fabric Heartbeat mechanism for Fabric jobs</li>
</ul>
</td>
</tr>
<tr>
<td width="150pxl">
<p>Fabric Jobs</p>
</td>
<td width="150pxl">
<ul>
<li>jobs</li>
</ul>
</td>
<td width="550pxl">
<ul>
<li>Thread pool size- the maximum number of jobs to be executed in parallel in a single Fabric node.</li>
<li>Archiving time- the number of hours to delete the Job record from k2_jobs table.</li>
</ul>
</td>
</tr>
<tr>
<td width="150pxl">
<p>Batch Process</p>
</td>
<td width="150pxl">
<ul>
<li>batch_process</li>
</ul>
</td>
<td width="550pxl">
<ul>
<li>MAX_WORKERS_PER_NODE parameter to set the maximum number of threads&nbsp;that are used in all batch process units (executions) together on this node.&nbsp;</li>
<li>Support setting MAX_WORKERS_PER_NODE=0 per node to avoid running a batch&nbsp;process on a specific node.&nbsp; &nbsp;&nbsp;</li>
</ul>
</td>
</tr>
<tr>
<td width="150pxl">
<p>Parsers</p>
</td>
<td width="150pxl">
<ul>
<li>parsers</li>
</ul>
</td>
<td width="550pxl">
<ul>
<li>PARSER_WRITING_TYPE - JDBC\LOADER - this parameter defines the method which will be&nbsp;used to load the data into Cassandra (when using yield in the parser). Loader</li>
</ul>
</td>
</tr>
<tr>
<td width="150pxl">
<p>IIDFinder</p>
</td>
<td width="150pxl">
<ul>
<li>finder</li>
</ul>
</td>
<td width="550pxl">
<ul>
<li>Enable ORPHANAGE job which handles Orphans record in the background.</li>
<li>Enable SWEEP job which sweeps the invalid cache entries.</li>
</ul>
</td>
</tr>
<tr>
<td width="150pxl">
<p>Cassandra Loader- loader configuration</p>
</td>
<td width="150pxl">
<ul>
<li>default_loader</li>
<li>parser_loader</li>
<li>batch_process_loader</li>
<li>iid_finder_loader</li>
</ul>
</td>
<td width="550pxl">
<p>Cassandra Loader configuration.</p>
<p>You can override the default setting of default_loader for parsers, batch processes, or IIDFinder activities.</p>
</td>
</tr>
<tr>
<td width="150pxl">
<p>Cassandra loader- session configuration</p>
</td>
<td width="150pxl">
<ul>
<li>loader_session&nbsp; &nbsp; &nbsp; &nbsp; &nbsp;</li>
</ul>
</td>
<td width="550pxl">
<p>Overrides the default_session for the sessions, created for Cassandra Loader operations (parsers, batch process, IIDFinder)</p>
</td>
</tr>
<tr>
<td width="150pxl">
<p>Common (reference) tables</p>
</td>
<td width="150pxl">
<ul>
<li>common_area_config</li>
<li>common_area_kafka_producer</li>
<li>common_area_kafka_consumer</li>
<li>kafka_ssl_properties</li>
<li>common_area_memory_queues_config&nbsp; &nbsp; &nbsp;</li>
</ul>
</td>
<td width="550pxl">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="150pxl">
<p>LUI Storage</p>
</td>
<td width="150pxl">
<ul>
<li>fabricdb</li>
<li>cassandra_entity_storage</li>
</ul>
</td>
<td width="550pxl">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="150pxl">
<p>Fabric Security Hardening</p>
</td>
<td width="150pxl">
<ul>
<li>encryption</li>
</ul>
</td>
<td width="550pxl">
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td width="150pxl">
<p>Change Data Capture (CDC) and Search</p>
</td>
<td width="150pxl">
<ul>
<li>cdc</li>
<li>cdc_data_publish</li>
<li>cdc_data_publish_ssl</li>
<li>cdc_data_consume</li>
<li>search_engine</li>
</ul>
</td>
<td width="550pxl">
<p>&nbsp;</p>
</td>
</tr>
</tbody>
</table>
<p>&nbsp;</p>

### node.id

This file lists the Fabric node identifiers for the Affinity mechanism. The following identifies can be set in the node.id file:

- **uuid**- if this parameter is not defined, Fabric automatically generates a value for the **uuid** while starting.
- **logical_id-** used to define an Affinity for Fabric jobs mechanism. The logical_id contains only letters and numbers. Several nodes can share the same logical_id. In addition, you can set several logical IDs for one node.  It is possible to define priority for each logical_id by adding several threads that will be allocated for each logical node. The number is concatenated to the logical_id name by colon. For example, the logical_id for a given node has the following values: A:2, B:3, and C:6. If there are 10 threads in the pool for this node, then the job using logical_id **C** as an Affinity will get higher priority on this node, as 6 out of the 10 threads will be allocated to this job.
- **cluster_id**- cluster identifier. The cluster_id is set to support a configuration of several Fabric clusters on one Cassandra cluster. The cluster_id is concatenated to each [keyspace](/articles/02_fabric_architecture/06_cassandra_keyspaces_for_fabric.md) name. For example- if the cluster_id is set to “fabric1”, then Fabric concatenates “_fabric1” to each keyspace.

 

## Update Configuration Files

### Update Config.ini and Node.id Files

Fabric adds a notification to k2fabric.log if the updates are loaded automatically to Fabric. If the changes requires a restart of Fabric node, Fabric adds a warning to the log file. 

Examples:

INFO  [FileChangeMonitor] 2020-06-07 18:30:40,207 c.k.f.c.i.Configurator - [LID1000000000496] Configurator changed fabric.DELETE_INSTANCES_IF_NOT_EXIST_COMMAND_ENABLED from false to true
INFO  [FileChangeMonitor] 2020-06-07 18:30:40,207 c.k.f.c.i.FileChangeMonitor - [LID1000000000496] config.ini was reloaded

WARN  [FileChangeMonitor] 2020-06-07 18:38:33,270 c.k.f.c.i.Configurator - [LID1000000000496] Configurator will not update fabricdb.MDB_DEFAULT_SCHEMA_CACHE_STORAGE_TYPE from com.k2view.cdbms.dao.CassandraEntityStorage to NONE at runtime.



### Update iifConfig.ini

<!--Ask Taha-->