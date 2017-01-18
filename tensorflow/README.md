# Tensorflow


## [Installation](https://www.tensorflow.org/get_started/os_setup) 

with GPU
```
pip install tensorflow-gpu
```

## Sanity Check

Check if GPU can be found

```python
from tensorflow.python.client import device_lib
device_lib.list_local_devices()
```

