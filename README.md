# Azure Callback for Tensorflow

This callback registers all metrics reported at the end of an epoch to Azure ML Studio in order to use Azure's native metric visualization.  This makes it easy to compare model performance in Azure and select best models.

For more information of usage see [Logging TensorFlow(Keras) metrics to Azure ML Studio in realtime](https://medium.com/p/14504a01cad8).

## Use

- Copy the `log_to_azure.py` file to your working directory.
- Import the callback class and add it to your model.  The callback requires that you pass it an azureml.core.Run object to define where to log the metrics.

```
from azureml.core import Run
from log_to_azure import LogToAzure
...

run = Run.get_context()
...

# add LogToAure custom Callback
callbacks = [LogToAzure(run)]

# fit model and store history
model.fit(train_generator, 
          validation_data=val_generator,
          callbacks=callbacks,
          epochs=10)
```
