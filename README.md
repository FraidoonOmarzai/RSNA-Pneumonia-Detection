# End-to-End-DL

## Steps:

1. Git clone the repository and Define template of the project

```bash
touch template.py
python3 template.py
```

2. define setup.py scripts (**The setup.py** is a module used to build and distribute Python packages. It typically contains information about the package)


3. Create environment and install dependencies

```bash
conda create -n dl-env python=3.9 -y
conda activate dl-env
pip install -r requirements.txt
```
4. define logger (The Logging is a means of tracking events that happen when some software runs)

5. define utils (The utils.py makes it easy to execute common tasks in Python scripts)

6. Run the notebook on google colab: 
* notebooks/Download_rsna_pneumonia.ipynb
* The above notebook download the dataset directly from the kaggle to google colab 
* We got a sample of images(400 images) in the .jpeg format after performing some preprocess steps
* finally we will convert the sample to zip file and store the sample in github repository

7. **Data Ingestion**
* config.yaml defined
* constants added
* 01_data_ingeston.ipynb created
* stage_01_data_ingeston.py created
 
8. **Prepare Base Model**
* config.yaml defined
* define params.yaml
* 02_prepare_base_model.ipynb created
* stage_02_prepare_base_model.py created

**Note: static methods** in Python are extremely similar to python class level methods, the difference being that a static method is bound to a class rather than the objects for that class. This means that a static method can be called without an object for that class.

9. **Model Training**
* config.yaml defined
* define params.yaml
* 03_model_traning.ipynb created
    * adding tensorboard callbacks
    
    ```bash
    tensorboard --logdir artifacts/prepare_callbacks/tensorboard_log_dir
    ```
    
    * adding checkpoint callbacks
* stage_03_model_traning.py created

10. **Model Evaluation**
* 04_model_evaluation.ipynb created
* stage_04_model_evaluation.py created

11. **DVC Section**

* add code to dvc.yaml and run the below commands
```bash
dvc init
dvc repro
dvc dag
```

12. **Webapp**

* create pipeline/prediction.py
* create index.html
* create app.py

13. **Docker file**

* create Dockerfile
* built a docker images
```bash
docker build -t pneumonia-app .
docker ps
docker images
```
* running our app
```bash
docker run -p 8080:8080 pneumonia-app
```

14. **Github Action(CI/CD)**

* create cicd1.yaml file and push the changes to github