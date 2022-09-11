# source:https://docs.microsoft.com/en-us/azure/architecture/patterns/

# data management
diffrent locations across multiple servers. Data consistency must be maintained and data will need to be sync across locations

## Cache aside
problem: use cache but impractiucal to allways be consistent.
sol: check data with cache. if not there add.
use: no read throug and write through aka its the main data store that it writes to and read 

## Event Sourcing pattern
When there need to be a clear trail for audit.
a datastore that only accept push. for example a postal service that need clear record or when you need to replay all events leading up toolbox

## Index Table pattern
creat second index in relational db to search quicker. extra table should adress data that searched often

## materialized-view
creat table with the data needed for queries to avoid calling multiple diffrent relational dbs

## sharding pattern