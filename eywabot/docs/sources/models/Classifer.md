### fit


```python
fit(X, Y)
```



Trains the model on given data.

__Arguments__

X: Input utterance(s). It could be:
- `str` (or `list` thereof)
- `Document` instance (or `list` thereof)

Y: Target labels. `str` (or `list` thereof). If `list`,
number of items in Y should be either 1 or equal
to number of utterances in X.

__Example__


Train a `Classifier` to classify a given utterance
to 2 classes: "greeting" and "bye":

Method 1 - fit on individual utterances:
```python
clf = Classifier()
clf.fit('hi', 'greeting')
clf.fit('good bye', 'bye')
clf.fit('hello', 'greeting')
clf.fit('see you later', 'bye')
```
Method 2 - fit on list of utterances:
```python
clf = Classifier()
greetings = ['hi', 'hello', 'hey']
bye = ['bye', 'good bye', 'see you later']
clf.fit(greetings, 'greeting')
clf.fit(bye, 'bye')
```
Method 3 - fit on list of utterances and labels:
```python
clf = Classifier()
input_data = ['hi', 'good bye', 'hello', 'hey', 'see you later']
target_labels = ['greeting', 'bye', 'greeting', 'greeting', 'bye']
clf.fit(input_data, target_labels)
```

----

### predict


```python
predict(x, return_scores=False)
```


Predicts labels for given input utterance(s)

__Arguments__

x: Input utterance(s). It could be:
- `str` (or `list`/`tuple` thereof)
- `Document` instance (or `list`/`tuple` thereof)

`return_scores`: `bool`. Default `False`.
If `True`, returns confidence for each class per utterance.
Else, returns label for class with highest confidence per utterance.

__Returns__

if `return_scores` is `True`:
if `x` is a single utterance:
    Returns a `list` of `tuple`s of the
    form (label, confidence) for each class,
    sorted by decreasing order of confidence.
if `x` is a `list`/`tuple` of utterances:
    Returns a `list` of results with 1 result per
    utterance. Each result will be a `list` of
    `tuple`s of the form (label, confidence) for
    each class, sorted by decreasing order of confidence.
if `return_scores` is `False`:
if `x` is a single utterance:
    Returns the predicted label as `str`.
if `x` is a `list`/`tuple` of utterances:
    Returns the predicted labels for utterances as `list` of
    `str`.
    
----

### evaluate


```python
evaluate(X=None, Y=None)
```


Evaluates the Classfier on given data.

Either both `X` and `Y` arguments should be provided
or both of them should be left unspecified (`None`).
If left unspecified, the cumilative data used to train
the `Classifier` will be used for evaluation .

__Arguments__

X: Input utterance(s). It could be:
- `str` (or `list` thereof)
- `Document` instance (or `list` thereof)

Y: Target labels. str (or list thereof). If list,
number of items in Y should be either 1 or equal
to number of utterances in X.

__Returns__

`tuple` of error(`float`) and accuracy(`float`)
    
----

### serialize


```python
serialize()
```


Serializes the `Classifier` object to a json
friendly config.

__Returns__

`dict`
    
----

### deserialize


```python
deserialize(config)
```


Deserializes a `Classifer` config to a `Classifier` instance.

__Arguments__

config: `dict`. `Classifier` config (generated by `Classifier.serialize`).

__Returns__

`Classifier` instance
    
----

### set_weights


```python
set_weights(weights)
```


Sets weights of the `Classifier` to given
values.

__Arguments__

weights: `list` of numpy arrays
    
----

### get_weights


```python
get_weights()
```


Returns weights of the `Classifier`.

__Returns__

`list` of numpy arrays
    