# Freshworks-Engineering-Assignment
# [key-value-ds](https://pypi.org/project/key-value-ds/)

##### File based Key-Value datastore

   Build a file-based key-value data store that supports the basic CRD (Create, Read, Delete) operations.

**Usage:**

###### Creating an instance
```
import key_value_ds
ds_instance = key_value_ds.get_instance()
```

Note: If `file_path` is provided in the `get_instance()` call, it will obtain lock on that file using `fcntl`. If object is created for the same file path twice, `BlockingIOError` is thrown.

###### To create an data
```
data_key = 'test_key'
data_value = {"value": 1}  # must be a JSON
time_to_live = 5*1000  # in milliseconds
ds_instance.create(data_key, data_value, ttl=time_to_live)
```

###### To retrieving the data
```
retrieve_key = 'test_key'
ds_instance.get(retrieve_key)   # returns {"value": 1} if retrieved within 5 seconds else ValueError
```

###### To delete the data
```
key_to_delete = 'test_key'
ds_instance.delete(key_to_delete)  # key-value is removed from the datastore
```

###### Delete all data
```
ds_instance.delete_all()
```
