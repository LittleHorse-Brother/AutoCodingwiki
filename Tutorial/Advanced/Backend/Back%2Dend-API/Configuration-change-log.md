# Summary

The current chat server has a caching mechanism and will not read the database all the time. Real-time synchronization of some databases is also achieved by relying on the change records of entities. Therefore, for certain entities, after adding/deleting/modifying, it is necessary to record the changelog in time. 

# Configure

In the `t_AutoCoding_Entity` table, there are several fields used to configure the change log

- IsRecordChangeLog

  Used to configure whether the entity needs to record the change log when adding/deleting/modifying operations. If it needs to be recorded, configure it to true, otherwise, configure it to false 

# Detail

For entities configured with `IsRecordChangeLog` to true, when adding/deleting/changing, the framework will automatically obtain the name, id and other information of the currently operating entity, generate the content of the change log table, and save it to the `t_LiveChat_ConfigurationChangeLog of the general library. `In the table 