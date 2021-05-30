
As the use case was using keras example notebook with imdb data, I let myself to use also the common mnist dataset, so hope it's fine for you :)

To run this application, clone the repo:

```bash
 git clone https://github.com/mlops-task/tf-serv.git
 cd tf-serv
 pip install -r requirements.txt
```

Install Tensorflow Serving
- [Link](https://www.tensorflow.org/tfx/serving/setup)


Start TF serving server
```
 docker run -p 8501:8501 --name tfserving_classifier \
 --mount type=bind,source=tf-server/img_classifier/,target=/models/img_classifier \
 -e MODEL_NAME=img_classifier -t tensorflow/serving
```

To make predictions, send HTTP request to server from another terminal.

```
  python predict.py
```

To retrain the model:
```
  python model.py
```
The proposed architecture draft can be found in file **possible_architecture.png**

Monitoring can be applied combining Cloudwatch metrics and Tensorboard.

Possible next steps for improvement in case of having more time:

* separate preprocessing steps in different modules
* adding unit tests
* adding logging 

Another approach of dealing with the problem is using model code with Tensorflow Estimator for Sagemaker. After deployment (the pipeline looks as following: api gateway + lambda + sagemaker estimator), the retraining/redeployment can be automated using step functions/airflow. For monitoring in this case Sagemaker Model Monitor can be used.
