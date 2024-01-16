



<a name='privacy'></a>

# Understanding Privacy Implications

Lucy is a powerful platform that gives you the flexibility to capture, manipulate and visualize all sorts of data.

This also means you need to be wary of the various privacy implications of storing and consuming such data.

As you will be designing your own orchestrations and deciding what to capture and what not to capture, you will have to decide what 
kind of data is acceptable to store and use from your own consumers, and how to purge it if required to do so.

This section will provide some guidelines for this and how we can help you.


## Data Stored by your Models Instances
When you build models with instances and define attributes, you are defining what kinds of data to capture and store.
All model instances are stored in persistent storage and backed-up regularly for safe keeping.

If you are capturing sensitive information that may need to be purged at some point, keep in mind that:

1. Deactivating your model instances will not be sufficient. Model instances that are deactivated stay in the system until they are garbage collected later
2. The best approach would be to overwrite that data as part of a action sequence that is specifically meant to purge data
3. Even overwriting your attributes may not be sufficient as we take regular backups of all your data for safe-keeping. If required, we can purge all backups from a given time range.
Note that you will lose all data in those backups.


## Metadata encoded in Models
This is more unlikely but it's possible that your model itself has sensitive data in it.
A common case would be if you hard-coded values to any blocks, or in javascript code, or used any sensitive account-names for connectors.

1. The best approach again is to overwrite the data by removing it from your model and saving it.
2. Keep in mind that Lucy maintains a full version history of your model, so you will have to delete all previous versions of the model as well. See [Version History](modeldesigner.md#versionhistory) for more information on how to do this.
3. All your models are backed-up as part of our regular database backups. Upon request, we can purge backups from a given time period.
4. If you have exported your models to your local computer or given to someone else, those will have to be deleted by you.


## Data stored in the debugger
The Lucy debugger is very useful to debug issues in your action sequences as it logs a wealth of information about executions.
One of the bits of data it logs is all the inputs and outputs to blocks. If your blocks are recieving or generating sensitive data of any kind, and you have debugging enabled for that action sequence, then that sensitive information
is likely stored in the debugger history for that model.

To deal with this:

1. Turn off debugging before you start using the action sequence for sensitive data
2. We can, on request, purge debug logs from specific actions.
3. Currently debug logs are also part of the regular database backups that are performed by us. So, on request, we will have to purge those backups as well.

## Data stored in logs
Errors from your model could have sensitive data in it and those are logged by internal logging system which we use for monitoring.
Upon request, we can purge log entries if we are given the (approximate) timestamps of the range of logs to purge.


If you have any questions, please `email us <mailto:security@iviva.com>` for more information.