# Training model

If you want to train model, set the `training` param in [`training.py`](https://github.com/t-ava/citibike-DNN/blob/master/training.py#L72) like below:

```python
training = True
```

* Default value is False to use pre-trained weights.

Then, run `python training.py` .

* Inputs: month, weekday, hour, station_id.
* Outputs: `pred` . number of devices in the station.
       * `pred` > 0: there are spare `pred` devices in the station.
       * `pred` < 0: require extra `|pred|` devices in the station.

We use MAE(Mean Absolute Error) to evaluate our model:
```
loss: 1.9897
```

# Run inference server

Run `python server.py`

## Request
```bash
curl -X POST -H 'Content-Type: application/json' http://127.0.0.1:5000/post -d '{"month": 12, "weekday": 4, "hour": 6, "ids": [2800, 123, 458, 1311, 3000, 1], "adj": 1}'
```
```
{"res":[0,1,-1,2,-2,0]}
```

`adj` is the flag of reflecting model loss:
* `adj` == 1: adjusting prediction results using loss (1.9897) .
* `adj` == 0: retuning bare prediction results.
