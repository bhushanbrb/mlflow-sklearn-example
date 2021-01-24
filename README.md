# Example MLflow project
https://www.mlflow.org/docs/latest/quickstart.html


`git clone https://github.com/mlflow/mlflow-example.git`

`cd mlflow-example`

^^^^^^change conda.yaml ^^^^^^^

```cat > conda.yaml << EOF
name: tutorial
channels:
  - defaults
dependencies:
  - numpy
  - pandas
  - scikit-learn
  - pip
  - pip:
    - mlflow
EOF

mlflow run . -P alpha=0.5

mlflow models serve -m runs:/<yourRUNID>/model --port 5001

example: 

mlflow models serve -m runs:/277d62e68aa947c290f2288cbdcf5c47/model --port 5001

CURL REQUEST : 

curl --request POST \
  --url http://127.0.0.1:5001/invocations \
  --header 'Content-Type: application/json; format=pandas-split' \
  --data '{"columns":["", "chlorides", "citric acid", "density", "fixed acidity", "free sulfur dioxide", "pH", "residual sugar", "sulphates", "total sulfur dioxide", "volatile acidity"],
 "data":[[7,0.27,0.36,20.7,0.045,45,170,1.001,3,0.45,8.8]]}'
 
 
 ex. GUNICRON Serve py file : /usr/local/Caskroom/miniconda/base/envs/mlflow-277d62e68aa947c290f2288cbdcf5c47/lib/python3.8/site-packages/mlflow/pyfunc
 ```
