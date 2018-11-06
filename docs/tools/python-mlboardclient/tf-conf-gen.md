
python-mlboardclient contains the **tf_conf** script which can be used
to generate **TensorFlow** config for distributed training:

For worker:

```bash
TF_CONF=$(tf_conf worker) python <train-script.py>
```

For parameter server:

```bash
TF_CONF=$(tf_conf ps) python <train-script.py>
```