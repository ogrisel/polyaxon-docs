## streaming_true_positives


```python
streaming_true_positives(predictions, labels, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Sum the weights of true_positives.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: The predicted values, a `Tensor` of arbitrary dimensions. Will
  be cast to `bool`.
- __labels__: The ground truth values, a `Tensor` whose dimensions must match
  `predictions`. Will be cast to `bool`.
- __weights__: Optional `Tensor` whose rank is either 0, or the same rank as
  `labels`, and must be broadcastable to `labels` (i.e., all dimensions
  must be either `1`, or the same as the corresponding `labels`
  dimension).
- __metrics_collections__: An optional list of collections that the metric
  value variable should be added to.
- __updates_collections__: An optional list of collections that the metric update
  ops should be added to.
- __name__: An optional variable_scope name.

  Returns:
- __value_tensor__: A `Tensor` representing the current value of the metric.
- __update_op__: An operation that accumulates the error from a batch of data.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, or if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  either `metrics_collections` or `updates_collections` are not a list or
  tuple.
  

----

## streaming_true_negatives


```python
streaming_true_negatives(predictions, labels, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Sum the weights of true_negatives.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: The predicted values, a `Tensor` of arbitrary dimensions. Will
  be cast to `bool`.
- __labels__: The ground truth values, a `Tensor` whose dimensions must match
  `predictions`. Will be cast to `bool`.
- __weights__: Optional `Tensor` whose rank is either 0, or the same rank as
  `labels`, and must be broadcastable to `labels` (i.e., all dimensions
  must be either `1`, or the same as the corresponding `labels`
  dimension).
- __metrics_collections__: An optional list of collections that the metric
  value variable should be added to.
- __updates_collections__: An optional list of collections that the metric update
  ops should be added to.
- __name__: An optional variable_scope name.

  Returns:
- __value_tensor__: A `Tensor` representing the current value of the metric.
- __update_op__: An operation that accumulates the error from a batch of data.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, or if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  either `metrics_collections` or `updates_collections` are not a list or
  tuple.
  

----

## streaming_false_positives


```python
streaming_false_positives(predictions, labels, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Sum the weights of false positives.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: The predicted values, a `Tensor` of arbitrary dimensions. Will
  be cast to `bool`.
- __labels__: The ground truth values, a `Tensor` whose dimensions must match
  `predictions`. Will be cast to `bool`.
- __weights__: Optional `Tensor` whose rank is either 0, or the same rank as
  `labels`, and must be broadcastable to `labels` (i.e., all dimensions
  must be either `1`, or the same as the corresponding `labels`
  dimension).
- __metrics_collections__: An optional list of collections that the metric
  value variable should be added to.
- __updates_collections__: An optional list of collections that the metric update
  ops should be added to.
- __name__: An optional variable_scope name.

  Returns:
- __value_tensor__: A `Tensor` representing the current value of the metric.
- __update_op__: An operation that accumulates the error from a batch of data.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, or if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  either `metrics_collections` or `updates_collections` are not a list or
  tuple.
  

----

## streaming_false_negatives


```python
streaming_false_negatives(predictions, labels, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes the total number of false negatives.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: The predicted values, a `Tensor` of arbitrary dimensions. Will
  be cast to `bool`.
- __labels__: The ground truth values, a `Tensor` whose dimensions must match
  `predictions`. Will be cast to `bool`.
- __weights__: Optional `Tensor` whose rank is either 0, or the same rank as
  `labels`, and must be broadcastable to `labels` (i.e., all dimensions
  must be either `1`, or the same as the corresponding `labels`
  dimension).
- __metrics_collections__: An optional list of collections that the metric
  value variable should be added to.
- __updates_collections__: An optional list of collections that the metric update
  ops should be added to.
- __name__: An optional variable_scope name.

  Returns:
- __value_tensor__: A `Tensor` representing the current value of the metric.
- __update_op__: An operation that accumulates the error from a batch of data.

  Raises:
- __ValueError__: If `weights` is not `None` and its shape doesn't match `values`,
  or if either `metrics_collections` or `updates_collections` are not a list
  or tuple.
  

----

## streaming_mean


```python
streaming_mean(values, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes the (weighted) mean of the given values.

  The `streaming_mean` function creates two local variables, `total` and `count`
  that are used to compute the average of `values`. This average is ultimately
  returned as `mean` which is an idempotent operation that simply divides
  `total` by `count`.

  For estimation of the metric  over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the `mean`.
  `update_op` increments `total` with the reduced sum of the product of `values`
  and `weights`, and it increments `count` with the reduced sum of `weights`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __values__: A `Tensor` of arbitrary dimensions.
- __weights__: `Tensor` whose rank is either 0, or the same rank as `values`, and
  must be broadcastable to `values` (i.e., all dimensions must be either
  `1`, or the same as the corresponding `values` dimension).
- __metrics_collections__: An optional list of collections that `mean`
  should be added to.
- __updates_collections__: An optional list of collections that `update_op`
  should be added to.
- __name__: An optional variable_scope name.

  Returns:
- __mean__: A `Tensor` representing the current mean, the value of `total` divided
  by `count`.
- __update_op__: An operation that increments the `total` and `count` variables
  appropriately and whose value matches `mean`.

  Raises:
- __ValueError__: If `weights` is not `None` and its shape doesn't match `values`,
  or if either `metrics_collections` or `updates_collections` are not a list
  or tuple.
  

----

## streaming_mean_tensor


```python
streaming_mean_tensor(values, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes the element-wise (weighted) mean of the given tensors.

  In contrast to the `streaming_mean` function which returns a scalar with the
  mean,  this function returns an average tensor with the same shape as the
  input tensors.

  The `streaming_mean_tensor` function creates two local variables,
  `total_tensor` and `count_tensor` that are used to compute the average of
  `values`. This average is ultimately returned as `mean` which is an idempotent
  operation that simply divides `total` by `count`.

  For estimation of the metric  over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the `mean`.
  `update_op` increments `total` with the reduced sum of the product of `values`
  and `weights`, and it increments `count` with the reduced sum of `weights`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __values__: A `Tensor` of arbitrary dimensions.
- __weights__: `Tensor` whose rank is either 0, or the same rank as `values`, and
  must be broadcastable to `values` (i.e., all dimensions must be either
  `1`, or the same as the corresponding `values` dimension).
- __metrics_collections__: An optional list of collections that `mean`
  should be added to.
- __updates_collections__: An optional list of collections that `update_op`
  should be added to.
- __name__: An optional variable_scope name.

  Returns:
- __mean__: A float `Tensor` representing the current mean, the value of `total`
  divided by `count`.
- __update_op__: An operation that increments the `total` and `count` variables
  appropriately and whose value matches `mean`.

  Raises:
- __ValueError__: If `weights` is not `None` and its shape doesn't match `values`,
  or if either `metrics_collections` or `updates_collections` are not a list
  or tuple.
  

----

## streaming_accuracy


```python
streaming_accuracy(predictions, labels, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Calculates how often `predictions` matches `labels`.

  The `streaming_accuracy` function creates two local variables, `total` and
  `count` that are used to compute the frequency with which `predictions`
  matches `labels`. This frequency is ultimately returned as `accuracy`: an
  idempotent operation that simply divides `total` by `count`.

  For estimation of the metric  over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the `accuracy`.
  Internally, an `is_correct` operation computes a `Tensor` with elements 1.0
  where the corresponding elements of `predictions` and `labels` match and 0.0
  otherwise. Then `update_op` increments `total` with the reduced sum of the
  product of `weights` and `is_correct`, and it increments `count` with the
  reduced sum of `weights`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: The predicted values, a `Tensor` of any shape.
- __labels__: The ground truth values, a `Tensor` whose shape matches
  `predictions`.
- __weights__: `Tensor` whose rank is either 0, or the same rank as `labels`, and
  must be broadcastable to `labels` (i.e., all dimensions must be either
  `1`, or the same as the corresponding `labels` dimension).
- __metrics_collections__: An optional list of collections that `accuracy` should
  be added to.
- __updates_collections__: An optional list of collections that `update_op` should
  be added to.
- __name__: An optional variable_scope name.

  Returns:
- __accuracy__: A `Tensor` representing the accuracy, the value of `total` divided
  by `count`.
- __update_op__: An operation that increments the `total` and `count` variables
  appropriately and whose value matches `accuracy`.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, or if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  either `metrics_collections` or `updates_collections` are not a list or
  tuple.
  

----

## streaming_precision


```python
streaming_precision(predictions, labels, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes the precision of the predictions with respect to the labels.

  The `streaming_precision` function creates two local variables,
  `true_positives` and `false_positives`, that are used to compute the
  precision. This value is ultimately returned as `precision`, an idempotent
  operation that simply divides `true_positives` by the sum of `true_positives`
  and `false_positives`.

  For estimation of the metric  over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the
  `precision`. `update_op` weights each prediction by the corresponding value in
  `weights`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: The predicted values, a `bool` `Tensor` of arbitrary shape.
- __labels__: The ground truth values, a `bool` `Tensor` whose dimensions must
  match `predictions`.
- __weights__: `Tensor` whose rank is either 0, or the same rank as `labels`, and
  must be broadcastable to `labels` (i.e., all dimensions must be either
  `1`, or the same as the corresponding `labels` dimension).
- __metrics_collections__: An optional list of collections that `precision` should
  be added to.
- __updates_collections__: An optional list of collections that `update_op` should
  be added to.
- __name__: An optional variable_scope name.

  Returns:
- __precision__: Scalar float `Tensor` with the value of `true_positives`
  divided by the sum of `true_positives` and `false_positives`.
- __update_op__: `Operation` that increments `true_positives` and
  `false_positives` variables appropriately and whose value matches
  `precision`.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, or if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  either `metrics_collections` or `updates_collections` are not a list or
  tuple.
  

----

## streaming_recall


```python
streaming_recall(predictions, labels, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes the recall of the predictions with respect to the labels.

  The `streaming_recall` function creates two local variables, `true_positives`
  and `false_negatives`, that are used to compute the recall. This value is
  ultimately returned as `recall`, an idempotent operation that simply divides
  `true_positives` by the sum of `true_positives`  and `false_negatives`.

  For estimation of the metric  over a stream of data, the function creates an
  `update_op` that updates these variables and returns the `recall`. `update_op`
  weights each prediction by the corresponding value in `weights`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: The predicted values, a `bool` `Tensor` of arbitrary shape.
- __labels__: The ground truth values, a `bool` `Tensor` whose dimensions must
  match `predictions`.
- __weights__: `Tensor` whose rank is either 0, or the same rank as `labels`, and
  must be broadcastable to `labels` (i.e., all dimensions must be either
  `1`, or the same as the corresponding `labels` dimension).
- __metrics_collections__: An optional list of collections that `recall` should
  be added to.
- __updates_collections__: An optional list of collections that `update_op` should
  be added to.
- __name__: An optional variable_scope name.

  Returns:
- __recall__: Scalar float `Tensor` with the value of `true_positives` divided
  by the sum of `true_positives` and `false_negatives`.
- __update_op__: `Operation` that increments `true_positives` and
  `false_negatives` variables appropriately and whose value matches
  `recall`.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, or if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  either `metrics_collections` or `updates_collections` are not a list or
  tuple.
  

----

## streaming_auc


```python
streaming_auc(predictions, labels, weights=None, num_thresholds=200, metrics_collections=None, updates_collections=None, curve='ROC', name=None)
```


Computes the approximate AUC via a Riemann sum.

  The `streaming_auc` function creates four local variables, `true_positives`,
  `true_negatives`, `false_positives` and `false_negatives` that are used to
  compute the AUC. To discretize the AUC curve, a linearly spaced set of
  thresholds is used to compute pairs of recall and precision values. The area
  under the ROC-curve is therefore computed using the height of the recall
  values by the false positive rate, while the area under the PR-curve is the
  computed using the height of the precision values by the recall.

  This value is ultimately returned as `auc`, an idempotent operation that
  computes the area under a discretized curve of precision versus recall values
  (computed using the aforementioned variables). The `num_thresholds` variable
  controls the degree of discretization with larger numbers of thresholds more
  closely approximating the true AUC. The quality of the approximation may vary
  dramatically depending on `num_thresholds`.

  For best results, `predictions` should be distributed approximately uniformly
  in the range [0, 1] and not peaked around 0 or 1. The quality of the AUC
  approximation may be poor if this is not the case.

  For estimation of the metric over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the `auc`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: A floating point `Tensor` of arbitrary shape and whose values
  are in the range `[0, 1]`.
- __labels__: A `bool` `Tensor` whose shape matches `predictions`.
- __weights__: `Tensor` whose rank is either 0, or the same rank as `labels`, and
  must be broadcastable to `labels` (i.e., all dimensions must be either
  `1`, or the same as the corresponding `labels` dimension).
- __num_thresholds__: The number of thresholds to use when discretizing the roc
  curve.
- __metrics_collections__: An optional list of collections that `auc` should be
  added to.
- __updates_collections__: An optional list of collections that `update_op` should
  be added to.
- __curve__: Specifies the name of the curve to be computed, 'ROC' [default] or
'PR' for the Precision-Recall-curve.
- __name__: An optional variable_scope name.

  Returns:
- __auc__: A scalar `Tensor` representing the current area-under-curve.
- __update_op__: An operation that increments the `true_positives`,
  `true_negatives`, `false_positives` and `false_negatives` variables
  appropriately and whose value matches `auc`.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, or if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  either `metrics_collections` or `updates_collections` are not a list or
  tuple.
  

----

## streaming_specificity_at_sensitivity


```python
streaming_specificity_at_sensitivity(predictions, labels, sensitivity, weights=None, num_thresholds=200, metrics_collections=None, updates_collections=None, name=None)
```


Computes the specificity at a given sensitivity.

  The `streaming_specificity_at_sensitivity` function creates four local
  variables, `true_positives`, `true_negatives`, `false_positives` and
  `false_negatives` that are used to compute the specificity at the given
  sensitivity value. The threshold for the given sensitivity value is computed
  and used to evaluate the corresponding specificity.

  For estimation of the metric over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the
  `specificity`. `update_op` increments the `true_positives`, `true_negatives`,
  `false_positives` and `false_negatives` counts with the weight of each case
  found in the `predictions` and `labels`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  For additional information about specificity and sensitivity, see the
  following: https://en.wikipedia.org/wiki/Sensitivity_and_specificity

  Args:
- __predictions__: A floating point `Tensor` of arbitrary shape and whose values
  are in the range `[0, 1]`.
- __labels__: A `bool` `Tensor` whose shape matches `predictions`.
- __sensitivity__: A scalar value in range `[0, 1]`.
- __weights__: `Tensor` whose rank is either 0, or the same rank as `labels`, and
  must be broadcastable to `labels` (i.e., all dimensions must be either
  `1`, or the same as the corresponding `labels` dimension).
- __num_thresholds__: The number of thresholds to use for matching the given
  sensitivity.
- __metrics_collections__: An optional list of collections that `specificity`
  should be added to.
- __updates_collections__: An optional list of collections that `update_op` should
  be added to.
- __name__: An optional variable_scope name.

  Returns:
- __specificity__: A scalar `Tensor` representing the specificity at the given
  `specificity` value.
- __update_op__: An operation that increments the `true_positives`,
  `true_negatives`, `false_positives` and `false_negatives` variables
  appropriately and whose value matches `specificity`.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  `sensitivity` is not between 0 and 1, or if either `metrics_collections`
  or `updates_collections` are not a list or tuple.
  

----

## streaming_sensitivity_at_specificity


```python
streaming_sensitivity_at_specificity(predictions, labels, specificity, weights=None, num_thresholds=200, metrics_collections=None, updates_collections=None, name=None)
```


Computes the specificity at a given sensitivity.

  The `streaming_sensitivity_at_specificity` function creates four local
  variables, `true_positives`, `true_negatives`, `false_positives` and
  `false_negatives` that are used to compute the sensitivity at the given
  specificity value. The threshold for the given specificity value is computed
  and used to evaluate the corresponding sensitivity.

  For estimation of the metric over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the
  `sensitivity`. `update_op` increments the `true_positives`, `true_negatives`,
  `false_positives` and `false_negatives` counts with the weight of each case
  found in the `predictions` and `labels`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  For additional information about specificity and sensitivity, see the
  following: https://en.wikipedia.org/wiki/Sensitivity_and_specificity

  Args:
- __predictions__: A floating point `Tensor` of arbitrary shape and whose values
  are in the range `[0, 1]`.
- __labels__: A `bool` `Tensor` whose shape matches `predictions`.
- __specificity__: A scalar value in range `[0, 1]`.
- __weights__: `Tensor` whose rank is either 0, or the same rank as `labels`, and
  must be broadcastable to `labels` (i.e., all dimensions must be either
  `1`, or the same as the corresponding `labels` dimension).
- __num_thresholds__: The number of thresholds to use for matching the given
  specificity.
- __metrics_collections__: An optional list of collections that `sensitivity`
  should be added to.
- __updates_collections__: An optional list of collections that `update_op` should
  be added to.
- __name__: An optional variable_scope name.

  Returns:
- __sensitivity__: A scalar `Tensor` representing the sensitivity at the given
  `specificity` value.
- __update_op__: An operation that increments the `true_positives`,
  `true_negatives`, `false_positives` and `false_negatives` variables
  appropriately and whose value matches `sensitivity`.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  `specificity` is not between 0 and 1, or if either `metrics_collections`
  or `updates_collections` are not a list or tuple.
  

----

## streaming_precision_at_thresholds


```python
streaming_precision_at_thresholds(predictions, labels, thresholds, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes precision values for different `thresholds` on `predictions`.

  The `streaming_precision_at_thresholds` function creates four local variables,
  `true_positives`, `true_negatives`, `false_positives` and `false_negatives`
  for various values of thresholds. `precision[i]` is defined as the total
  weight of values in `predictions` above `thresholds[i]` whose corresponding
  entry in `labels` is `True`, divided by the total weight of values in
  `predictions` above `thresholds[i]` (`true_positives[i] / (true_positives[i] +
  false_positives[i])`).

  For estimation of the metric over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the
  `precision`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: A floating point `Tensor` of arbitrary shape and whose values
  are in the range `[0, 1]`.
- __labels__: A `bool` `Tensor` whose shape matches `predictions`.
- __thresholds__: A python list or tuple of float thresholds in `[0, 1]`.
- __weights__: `Tensor` whose rank is either 0, or the same rank as `labels`, and
  must be broadcastable to `labels` (i.e., all dimensions must be either
  `1`, or the same as the corresponding `labels` dimension).
- __metrics_collections__: An optional list of collections that `auc` should be
  added to.
- __updates_collections__: An optional list of collections that `update_op` should
  be added to.
- __name__: An optional variable_scope name.

  Returns:
- __precision__: A float `Tensor` of shape `[len(thresholds)]`.
- __update_op__: An operation that increments the `true_positives`,
  `true_negatives`, `false_positives` and `false_negatives` variables that
  are used in the computation of `precision`.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, or if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  either `metrics_collections` or `updates_collections` are not a list or
  tuple.
  

----

## streaming_recall_at_thresholds


```python
streaming_recall_at_thresholds(predictions, labels, thresholds, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes various recall values for different `thresholds` on `predictions`.

  The `streaming_recall_at_thresholds` function creates four local variables,
  `true_positives`, `true_negatives`, `false_positives` and `false_negatives`
  for various values of thresholds. `recall[i]` is defined as the total weight
  of values in `predictions` above `thresholds[i]` whose corresponding entry in
  `labels` is `True`, divided by the total weight of `True` values in `labels`
  (`true_positives[i] / (true_positives[i] + false_negatives[i])`).

  For estimation of the metric over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the `recall`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: A floating point `Tensor` of arbitrary shape and whose values
  are in the range `[0, 1]`.
- __labels__: A `bool` `Tensor` whose shape matches `predictions`.
- __thresholds__: A python list or tuple of float thresholds in `[0, 1]`.
- __weights__: `Tensor` whose rank is either 0, or the same rank as `labels`, and
  must be broadcastable to `labels` (i.e., all dimensions must be either
  `1`, or the same as the corresponding `labels` dimension).
- __metrics_collections__: An optional list of collections that `recall` should be
  added to.
- __updates_collections__: An optional list of collections that `update_op` should
  be added to.
- __name__: An optional variable_scope name.

  Returns:
- __recall__: A float `Tensor` of shape `[len(thresholds)]`.
- __update_op__: An operation that increments the `true_positives`,
  `true_negatives`, `false_positives` and `false_negatives` variables that
  are used in the computation of `recall`.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, or if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  either `metrics_collections` or `updates_collections` are not a list or
  tuple.
  

----

## streaming_sparse_recall_at_k


```python
streaming_sparse_recall_at_k(predictions, labels, k, class_id=None, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes recall@k of the predictions with respect to sparse labels.

  If `class_id` is not specified, we'll calculate recall as the ratio of true
  positives (i.e., correct predictions, items in the top `k` highest
  `predictions` that are found in the corresponding row in `labels`) to
  actual positives (the full `labels` row).
  If `class_id` is specified, we calculate recall by considering only the rows
  in the batch for which `class_id` is in `labels`, and computing the
  fraction of them for which `class_id` is in the corresponding row in
  `labels`.

  `streaming_sparse_recall_at_k` creates two local variables,
  `true_positive_at_<k>` and `false_negative_at_<k>`, that are used to compute
  the recall_at_k frequency. This frequency is ultimately returned as
  `recall_at_<k>`: an idempotent operation that simply divides
  `true_positive_at_<k>` by total (`true_positive_at_<k>` +
  `false_negative_at_<k>`).

  For estimation of the metric over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the
  `recall_at_<k>`. Internally, a `top_k` operation computes a `Tensor`
  indicating the top `k` `predictions`. Set operations applied to `top_k` and
  `labels` calculate the true positives and false negatives weighted by
  `weights`. Then `update_op` increments `true_positive_at_<k>` and
  `false_negative_at_<k>` using these values.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: Float `Tensor` with shape [D1, ... DN, num_classes] where
  N >= 1. Commonly, N=1 and predictions has shape [batch size, num_classes].
  The final dimension contains the logit values for each class. [D1, ... DN]
  must match `labels`.
- __labels__: `int64` `Tensor` or `SparseTensor` with shape
  [D1, ... DN, num_labels], where N >= 1 and num_labels is the number of
  target classes for the associated prediction. Commonly, N=1 and `labels`
  has shape [batch_size, num_labels]. [D1, ... DN] must match `predictions`.
  Values should be in range [0, num_classes), where num_classes is the last
  dimension of `predictions`. Values outside this range always count
  towards `false_negative_at_<k>`.
- __k__: Integer, k for @k metric.
- __class_id__: Integer class ID for which we want binary metrics. This should be
  in range [0, num_classes), where num_classes is the last dimension of
  `predictions`. If class_id is outside this range, the method returns NAN.
- __weights__: `Tensor` whose rank is either 0, or n-1, where n is the rank of
  `labels`. If the latter, it must be broadcastable to `labels` (i.e., all
  dimensions must be either `1`, or the same as the corresponding `labels`
  dimension).
- __metrics_collections__: An optional list of collections that values should
  be added to.
- __updates_collections__: An optional list of collections that updates should
  be added to.
- __name__: Name of new update operation, and namespace for other dependent ops.

  Returns:
- __recall__: Scalar `float64` `Tensor` with the value of `true_positives` divided
  by the sum of `true_positives` and `false_negatives`.
- __update_op__: `Operation` that increments `true_positives` and
  `false_negatives` variables appropriately, and whose value matches
  `recall`.

  Raises:
- __ValueError__: If `weights` is not `None` and its shape doesn't match
`predictions`, or if either `metrics_collections` or `updates_collections`
are not a list or tuple.
  

----

## streaming_sparse_precision_at_k


```python
streaming_sparse_precision_at_k(predictions, labels, k, class_id=None, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes precision@k of the predictions with respect to sparse labels.

  If `class_id` is not specified, we calculate precision as the ratio of true
  positives (i.e., correct predictions, items in the top `k` highest
  `predictions` that are found in the corresponding row in `labels`) to
  positives (all top `k` `predictions`).
  If `class_id` is specified, we calculate precision by considering only the
  rows in the batch for which `class_id` is in the top `k` highest
  `predictions`, and computing the fraction of them for which `class_id` is
  in the corresponding row in `labels`.

  We expect precision to decrease as `k` increases.

  `streaming_sparse_precision_at_k` creates two local variables,
  `true_positive_at_<k>` and `false_positive_at_<k>`, that are used to compute
  the precision@k frequency. This frequency is ultimately returned as
  `precision_at_<k>`: an idempotent operation that simply divides
  `true_positive_at_<k>` by total (`true_positive_at_<k>` +
  `false_positive_at_<k>`).

  For estimation of the metric over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the
  `precision_at_<k>`. Internally, a `top_k` operation computes a `Tensor`
  indicating the top `k` `predictions`. Set operations applied to `top_k` and
  `labels` calculate the true positives and false positives weighted by
  `weights`. Then `update_op` increments `true_positive_at_<k>` and
  `false_positive_at_<k>` using these values.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: Float `Tensor` with shape [D1, ... DN, num_classes] where
  N >= 1. Commonly, N=1 and predictions has shape [batch size, num_classes].
  The final dimension contains the logit values for each class. [D1, ... DN]
  must match `labels`.
- __labels__: `int64` `Tensor` or `SparseTensor` with shape
  [D1, ... DN, num_labels], where N >= 1 and num_labels is the number of
  target classes for the associated prediction. Commonly, N=1 and `labels`
  has shape [batch_size, num_labels]. [D1, ... DN] must match
  `predictions`. Values should be in range [0, num_classes), where
  num_classes is the last dimension of `predictions`. Values outside this
  range are ignored.
- __k__: Integer, k for @k metric.
- __class_id__: Integer class ID for which we want binary metrics. This should be
  in range [0, num_classes], where num_classes is the last dimension of
  `predictions`. If `class_id` is outside this range, the method returns
  NAN.
- __weights__: `Tensor` whose rank is either 0, or n-1, where n is the rank of
  `labels`. If the latter, it must be broadcastable to `labels` (i.e., all
  dimensions must be either `1`, or the same as the corresponding `labels`
  dimension).
- __metrics_collections__: An optional list of collections that values should
  be added to.
- __updates_collections__: An optional list of collections that updates should
  be added to.
- __name__: Name of new update operation, and namespace for other dependent ops.

  Returns:
- __precision__: Scalar `float64` `Tensor` with the value of `true_positives`
  divided by the sum of `true_positives` and `false_positives`.
- __update_op__: `Operation` that increments `true_positives` and
  `false_positives` variables appropriately, and whose value matches
  `precision`.

  Raises:
- __ValueError__: If `weights` is not `None` and its shape doesn't match
  `predictions`, or if either `metrics_collections` or `updates_collections`
  are not a list or tuple.
  

----

## streaming_mean_absolute_error


```python
streaming_mean_absolute_error(predictions, labels, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes the mean absolute error between the labels and predictions.

  The `streaming_mean_absolute_error` function creates two local variables,
  `total` and `count` that are used to compute the mean absolute error. This
  average is weighted by `weights`, and it is ultimately returned as
  `mean_absolute_error`: an idempotent operation that simply divides `total` by
  `count`.

  For estimation of the metric over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the
  `mean_absolute_error`. Internally, an `absolute_errors` operation computes the
  absolute value of the differences between `predictions` and `labels`. Then
  `update_op` increments `total` with the reduced sum of the product of
  `weights` and `absolute_errors`, and it increments `count` with the reduced
  sum of `weights`

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: A `Tensor` of arbitrary shape.
- __labels__: A `Tensor` of the same shape as `predictions`.
- __weights__: Optional `Tensor` indicating the frequency with which an example is
  sampled. Rank must be 0, or the same rank as `labels`, and must be
  broadcastable to `labels` (i.e., all dimensions must be either `1`, or
  the same as the corresponding `labels` dimension).
- __metrics_collections__: An optional list of collections that
  `mean_absolute_error` should be added to.
- __updates_collections__: An optional list of collections that `update_op` should
  be added to.
- __name__: An optional variable_scope name.

  Returns:
- __mean_absolute_error__: A `Tensor` representing the current mean, the value of
  `total` divided by `count`.
- __update_op__: An operation that increments the `total` and `count` variables
  appropriately and whose value matches `mean_absolute_error`.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, or if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  either `metrics_collections` or `updates_collections` are not a list or
  tuple.
  

----

## streaming_mean_relative_error


```python
streaming_mean_relative_error(predictions, labels, normalizer, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes the mean relative error by normalizing with the given values.

  The `streaming_mean_relative_error` function creates two local variables,
  `total` and `count` that are used to compute the mean relative absolute error.
  This average is weighted by `weights`, and it is ultimately returned as
  `mean_relative_error`: an idempotent operation that simply divides `total` by
  `count`.

  For estimation of the metric over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the
  `mean_reative_error`. Internally, a `relative_errors` operation divides the
  absolute value of the differences between `predictions` and `labels` by the
  `normalizer`. Then `update_op` increments `total` with the reduced sum of the
  product of `weights` and `relative_errors`, and it increments `count` with the
  reduced sum of `weights`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: A `Tensor` of arbitrary shape.
- __labels__: A `Tensor` of the same shape as `predictions`.
- __normalizer__: A `Tensor` of the same shape as `predictions`.
- __weights__: Optional `Tensor` indicating the frequency with which an example is
  sampled. Rank must be 0, or the same rank as `labels`, and must be
  broadcastable to `labels` (i.e., all dimensions must be either `1`, or
  the same as the corresponding `labels` dimension).
- __metrics_collections__: An optional list of collections that
  `mean_relative_error` should be added to.
- __updates_collections__: An optional list of collections that `update_op` should
  be added to.
- __name__: An optional variable_scope name.

  Returns:
- __mean_relative_error__: A `Tensor` representing the current mean, the value of
  `total` divided by `count`.
- __update_op__: An operation that increments the `total` and `count` variables
  appropriately and whose value matches `mean_relative_error`.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, or if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  either `metrics_collections` or `updates_collections` are not a list or
  tuple.
  

----

## streaming_mean_squared_error


```python
streaming_mean_squared_error(predictions, labels, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes the mean squared error between the labels and predictions.

  The `streaming_mean_squared_error` function creates two local variables,
  `total` and `count` that are used to compute the mean squared error.
  This average is weighted by `weights`, and it is ultimately returned as
  `mean_squared_error`: an idempotent operation that simply divides `total` by
  `count`.

  For estimation of the metric over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the
  `mean_squared_error`. Internally, a `squared_error` operation computes the
  element-wise square of the difference between `predictions` and `labels`. Then
  `update_op` increments `total` with the reduced sum of the product of
  `weights` and `squared_error`, and it increments `count` with the reduced sum
  of `weights`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: A `Tensor` of arbitrary shape.
- __labels__: A `Tensor` of the same shape as `predictions`.
- __weights__: Optional `Tensor` indicating the frequency with which an example is
  sampled. Rank must be 0, or the same rank as `labels`, and must be
  broadcastable to `labels` (i.e., all dimensions must be either `1`, or
  the same as the corresponding `labels` dimension).
- __metrics_collections__: An optional list of collections that
  `mean_squared_error` should be added to.
- __updates_collections__: An optional list of collections that `update_op` should
  be added to.
- __name__: An optional variable_scope name.

  Returns:
- __mean_squared_error__: A `Tensor` representing the current mean, the value of
  `total` divided by `count`.
- __update_op__: An operation that increments the `total` and `count` variables
  appropriately and whose value matches `mean_squared_error`.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, or if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  either `metrics_collections` or `updates_collections` are not a list or
  tuple.
  

----

## streaming_root_mean_squared_error


```python
streaming_root_mean_squared_error(predictions, labels, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes the root mean squared error between the labels and predictions.

  The `streaming_root_mean_squared_error` function creates two local variables,
  `total` and `count` that are used to compute the root mean squared error.
  This average is weighted by `weights`, and it is ultimately returned as
  `root_mean_squared_error`: an idempotent operation that takes the square root
  of the division of `total` by `count`.

  For estimation of the metric over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the
  `root_mean_squared_error`. Internally, a `squared_error` operation computes
  the element-wise square of the difference between `predictions` and `labels`.
  Then `update_op` increments `total` with the reduced sum of the product of
  `weights` and `squared_error`, and it increments `count` with the reduced sum
  of `weights`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: A `Tensor` of arbitrary shape.
- __labels__: A `Tensor` of the same shape as `predictions`.
- __weights__: Optional `Tensor` indicating the frequency with which an example is
  sampled. Rank must be 0, or the same rank as `labels`, and must be
  broadcastable to `labels` (i.e., all dimensions must be either `1`, or
  the same as the corresponding `labels` dimension).
- __metrics_collections__: An optional list of collections that
  `root_mean_squared_error` should be added to.
- __updates_collections__: An optional list of collections that `update_op` should
  be added to.
- __name__: An optional variable_scope name.

  Returns:
- __root_mean_squared_error__: A `Tensor` representing the current mean, the value
  of `total` divided by `count`.
- __update_op__: An operation that increments the `total` and `count` variables
  appropriately and whose value matches `root_mean_squared_error`.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, or if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  either `metrics_collections` or `updates_collections` are not a list or
  tuple.
  

----

## streaming_covariance


```python
streaming_covariance(predictions, labels, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes the unbiased sample covariance between `predictions` and `labels`.

  The `streaming_covariance` function creates four local variables,
  `comoment`, `mean_prediction`, `mean_label`, and `count`, which are used to
  compute the sample covariance between predictions and labels across multiple
  batches of data. The covariance is ultimately returned as an idempotent
  operation that simply divides `comoment` by `count` - 1. We use `count` - 1
  in order to get an unbiased estimate.

  The algorithm used for this online computation is described in
  https://en.wikipedia.org/wiki/Algorithms_for_calculating_variance.
  Specifically, the formula used to combine two sample comoments is
  `C_AB = C_A + C_B + (E[x_A] - E[x_B]) * (E[y_A] - E[y_B]) * n_A * n_B / n_AB`
  The comoment for a single batch of data is simply
  `sum((x - E[x]) * (y - E[y]))`, optionally weighted.

  If `weights` is not None, then it is used to compute weighted comoments,
  means, and count. NOTE: these weights are treated as "frequency weights", as
  opposed to "reliability weights". See discussion of the difference on
  https://wikipedia.org/wiki/Weighted_arithmetic_mean#Weighted_sample_variance

  To facilitate the computation of covariance across multiple batches of data,
  the function creates an `update_op` operation, which updates underlying
  variables and returns the updated covariance.

  Args:
- __predictions__: A `Tensor` of arbitrary size.
- __labels__: A `Tensor` of the same size as `predictions`.
- __weights__: Optional `Tensor` indicating the frequency with which an example is
  sampled. Rank must be 0, or the same rank as `labels`, and must be
  broadcastable to `labels` (i.e., all dimensions must be either `1`, or
  the same as the corresponding `labels` dimension).
- __metrics_collections__: An optional list of collections that the metric
  value variable should be added to.
- __updates_collections__: An optional list of collections that the metric update
  ops should be added to.
- __name__: An optional variable_scope name.

  Returns:
- __covariance__: A `Tensor` representing the current unbiased sample covariance,
  `comoment` / (`count` - 1).
- __update_op__: An operation that updates the local variables appropriately.

  Raises:
- __ValueError__: If labels and predictions are of different sizes or if either
  `metrics_collections` or `updates_collections` are not a list or tuple.
  

----

## streaming_pearson_correlation


```python
streaming_pearson_correlation(predictions, labels, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes Pearson correlation coefficient between `predictions`, `labels`.

  The `streaming_pearson_correlation` function delegates to
  `streaming_covariance` the tracking of three [co]variances:

  - `streaming_covariance(predictions, labels)`, i.e. covariance
  - `streaming_covariance(predictions, predictions)`, i.e. variance
  - `streaming_covariance(labels, labels)`, i.e. variance

  The product-moment correlation ultimately returned is an idempotent operation
  `cov(predictions, labels) / sqrt(var(predictions) * var(labels))`. To
  facilitate correlation computation across multiple batches, the function
  groups the `update_op`s of the underlying streaming_covariance and returns an
  `update_op`.

  If `weights` is not None, then it is used to compute a weighted correlation.
  NOTE: these weights are treated as "frequency weights", as opposed to
  "reliability weights". See discussion of the difference on
  https://wikipedia.org/wiki/Weighted_arithmetic_mean#Weighted_sample_variance

  Args:
- __predictions__: A `Tensor` of arbitrary size.
- __labels__: A `Tensor` of the same size as predictions.
- __weights__: Optional `Tensor` indicating the frequency with which an example is
  sampled. Rank must be 0, or the same rank as `labels`, and must be
  broadcastable to `labels` (i.e., all dimensions must be either `1`, or
  the same as the corresponding `labels` dimension).
- __metrics_collections__: An optional list of collections that the metric
  value variable should be added to.
- __updates_collections__: An optional list of collections that the metric update
  ops should be added to.
- __name__: An optional variable_scope name.

  Returns:
- __pearson_r__: A `Tensor` representing the current Pearson product-moment
  correlation coefficient, the value of
  `cov(predictions, labels) / sqrt(var(predictions) * var(labels))`.
- __update_op__: An operation that updates the underlying variables appropriately.

  Raises:
- __ValueError__: If `labels` and `predictions` are of different sizes, or if
  `weights` is the wrong size, or if either `metrics_collections` or
  `updates_collections` are not a `list` or `tuple`.
  

----

## streaming_mean_cosine_distance


```python
streaming_mean_cosine_distance(predictions, labels, dim, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes the cosine distance between the labels and predictions.

  The `streaming_mean_cosine_distance` function creates two local variables,
  `total` and `count` that are used to compute the average cosine distance
  between `predictions` and `labels`. This average is weighted by `weights`,
  and it is ultimately returned as `mean_distance`, which is an idempotent
  operation that simply divides `total` by `count`.

  For estimation of the metric over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the
  `mean_distance`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: A `Tensor` of the same shape as `labels`.
- __labels__: A `Tensor` of arbitrary shape.
- __dim__: The dimension along which the cosine distance is computed.
- __weights__: An optional `Tensor` whose shape is broadcastable to `predictions`,
  and whose dimension `dim` is 1.
- __metrics_collections__: An optional list of collections that the metric
  value variable should be added to.
- __updates_collections__: An optional list of collections that the metric update
  ops should be added to.
- __name__: An optional variable_scope name.

  Returns:
- __mean_distance__: A `Tensor` representing the current mean, the value of
  `total` divided by `count`.
- __update_op__: An operation that increments the `total` and `count` variables
  appropriately.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, or if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  either `metrics_collections` or `updates_collections` are not a list or
  tuple.
  

----

## streaming_percentage_less


```python
streaming_percentage_less(values, threshold, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Computes the percentage of values less than the given threshold.

  The `streaming_percentage_less` function creates two local variables,
  `total` and `count` that are used to compute the percentage of `values` that
  fall below `threshold`. This rate is weighted by `weights`, and it is
  ultimately returned as `percentage` which is an idempotent operation that
  simply divides `total` by `count`.

  For estimation of the metric over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the
  `percentage`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __values__: A numeric `Tensor` of arbitrary size.
- __threshold__: A scalar threshold.
- __weights__: An optional `Tensor` whose shape is broadcastable to `values`.
- __metrics_collections__: An optional list of collections that the metric
  value variable should be added to.
- __updates_collections__: An optional list of collections that the metric update
  ops should be added to.
- __name__: An optional variable_scope name.

  Returns:
- __percentage__: A `Tensor` representing the current mean, the value of `total`
  divided by `count`.
- __update_op__: An operation that increments the `total` and `count` variables
  appropriately.

  Raises:
- __ValueError__: If `weights` is not `None` and its shape doesn't match `values`,
  or if either `metrics_collections` or `updates_collections` are not a list
  or tuple.
  

----

## streaming_mean_iou


```python
streaming_mean_iou(predictions, labels, num_classes, weights=None, metrics_collections=None, updates_collections=None, name=None)
```


Calculate per-step mean Intersection-Over-Union (mIOU).

  Mean Intersection-Over-Union is a common evaluation metric for
  semantic image segmentation, which first computes the IOU for each
  semantic class and then computes the average over classes.
  IOU is defined as follows:
IOU = true_positive / (true_positive + false_positive + false_negative).
  The predictions are accumulated in a confusion matrix, weighted by `weights`,
  and mIOU is then calculated from it.

  For estimation of the metric over a stream of data, the function creates an
  `update_op` operation that updates these variables and returns the `mean_iou`.

  If `weights` is `None`, weights default to 1. Use weights of 0 to mask values.

  Args:
- __predictions__: A `Tensor` of prediction results for semantic labels, whose
  shape is [batch size] and type `int32` or `int64`. The tensor will be
  flattened, if its rank > 1.
- __labels__: A `Tensor` of ground truth labels with shape [batch size] and of
  type `int32` or `int64`. The tensor will be flattened, if its rank > 1.
- __num_classes__: The possible number of labels the prediction task can
  have. This value must be provided, since a confusion matrix of
  dimension = [num_classes, num_classes] will be allocated.
- __weights__: An optional `Tensor` whose shape is broadcastable to `predictions`.
- __metrics_collections__: An optional list of collections that `mean_iou`
  should be added to.
- __updates_collections__: An optional list of collections `update_op` should be
  added to.
- __name__: An optional variable_scope name.

  Returns:
- __mean_iou__: A `Tensor` representing the mean intersection-over-union.
- __update_op__: An operation that increments the confusion matrix.

  Raises:
- __ValueError__: If `predictions` and `labels` have mismatched shapes, or if
  `weights` is not `None` and its shape doesn't match `predictions`, or if
  either `metrics_collections` or `updates_collections` are not a list or
  tuple.
  