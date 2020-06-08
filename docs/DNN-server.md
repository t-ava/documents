# Clone & Install requirements

```
git clone https://github.com/t-ava/citibike-DNN.git
```

```
pip install -r requirements.txt
```

# Preprocessing data

Download citibike data via [Link](https://www.citibikenyc.com/system-data).
* Download `201901-citibike-tripdata.csv` ~ `201912-citibike-tripdata.csv` at `./data/` .

Then, run `python preprocess.py` .

# Training model

You can skip this **# Training model** with `citibike_DNN_model.h5` (pre-trained weights) . Go **# Evaluation**.

If you want to train model, set the `training` param in [`training.py`](https://github.com/t-ava/citibike-DNN/blob/master/training.py#L72) like below:

```python
training = True
```

* Default value is False to use pre-trained weights.

Then, run `python training.py` . You need preprocessed data in `./data/` to train model.

* Inputs: month, weekday, hour, station_id.
* Outputs: `pred` . number of devices in the station.
     * `pred` > 0: there are spare `pred` devices in the station.
     * `pred` < 0: require extra `|pred|` devices in the station.

We use MAE(Mean Absolute Error) to evaluate our model:
```
loss: 1.9897
```

# Evaluation

Run `python training.py` with

```python
training = True
```

as same as a [default value](https://github.com/t-ava/citibike-DNN/blob/master/training.py#L72).

```
>>> loading model complete
array([[ 1.000e+01,  0.000e+00,  9.000e+00,  2.230e+02,  0.000e+00],
       [ 9.000e+00,  3.000e+00,  0.000e+00,  4.330e+02,  0.000e+00],
       [ 1.000e+01,  6.000e+00,  9.000e+00,  7.400e+01,  0.000e+00],
       [ 4.000e+00,  0.000e+00,  1.000e+01,  2.072e+03,  1.000e+00],
       [ 8.000e+00,  4.000e+00,  1.500e+01,  3.737e+03,  0.000e+00],
       [ 3.000e+00,  0.000e+00,  2.200e+01,  8.060e+02,  2.000e+00],
       [ 1.200e+01,  5.000e+00,  5.000e+00,  3.086e+03, -0.000e+00],
       [ 1.200e+01,  4.000e+00,  6.000e+00,  2.800e+02, -0.000e+00],
       [ 1.100e+01,  0.000e+00,  2.200e+01,  2.955e+03,  0.000e+00],
       [ 6.000e+00,  0.000e+00,  1.300e+01,  2.402e+03,  0.000e+00]])
```

[month, weekday, hour, id, prediction_result] per row.

# Run inference server

Run `python server.py`

Port number: 8327 as default.

## Request
```bash
curl -X POST -H 'Content-Type: application/json' http://127.0.0.1:8327/post -d '{"month": 12, "weekday": 4, "hour": 6, "ids": [2800, 123, 458, 1311, 3000, 1], "adj": 1}'
```
```
{"res":[0,1,-1,2,-2,0]}
```

`adj` is the flag of reflecting model loss:
* `adj` == 1: adjusting prediction results using loss (1.9897) .
* `adj` == 0: retuning bare prediction results.
