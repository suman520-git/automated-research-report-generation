# Automated-Research-Report-Generation

Automatic generation of the report on the given "topic name" by the user with Agentic AI(Langgraph framework).

##  Project Overview

1.There are three  stategraphs named "ResearchGraphState" ,"InterviewState",and "GenerateAnalystsState" defined for complete workflow(Orchestration).
  Among three graphs ,"ResearchGraphState" is main graph and reamining two are subgraphs of the main graph. Fileds defined in the subgraphs are the subset of fileds
  defined in the maion graph.

2.From the first workflow "GenerateAnalystsState" , Analysts will be created with given topic name and number of analysts given by user input  with human feedback to 
  conduct interview with experts.

3.From the "InterviewState" workflow , based on number of Analysts and topic name , same number of questions will be generated to be asked , send to Tavily search and wikipedia search  to generate answers .All the genearated answers are saved as interview and sections independently

4.From the main graph "ResearchGraphState" ,with all the generated sections and content , final report will be generated with introduction, content and conclusion.

5.we can download the final report in the pdf and docx format.

6.complete workflow
![image alt](https://github.com/suman520-git/automated-research-report-generation/blob/main/workflow.png?raw=true)

## Project Structure
```
automated-research-report-generation   
├─ research_and_analyst                
│  ├─ api                              
│  │  ├─ models                        
│  │  │  ├─ request_models.py          
│  │  │  └─ __init__.py                
│  │  ├─ routes                        
│  │  │  ├─ report_routes.py           
│  │  │  └─ __init__.py                
│  │  ├─ services                      
│  │  │  ├─ report_service.py          
│  │  │  └─ __init__.py                
│  │  ├─ templates                     
│  │  │  ├─ dashboard.html             
│  │  │  ├─ login.html                 
│  │  │  ├─ report_progress.html       
│  │  │  └─ signup.html                
│  │  ├─ main.py                       
│  │  └─ __init__.py                   
│  ├─ config                           
│  │  └─ configuration.yaml            
│  ├─ database                         
│  │  ├─ db_config.py                  
│  │  └─ __init__.py                   
│  ├─ exception                        
│  │  ├─ custom_exception.py           
│  │  └─ __init__.py                   
│  ├─ logger                           
│  │  ├─ custom_logger.py              
│  │  └─ __init__.py                   
│  ├─ notebook                         
│  │  └─ test.ipynb                    
│  ├─ prompt_lib                       
│  │  ├─ prompts.py                    
│  │  ├─ prompt_locator.py             
│  │  └─ __init__.py                   
│  ├─ router                           
│  │  └─ __init__.py                   
│  ├─ schemas                          
│  │  ├─ models.py                     
│  │  └─ __init__.py                   
│  ├─ utils                            
│  │  ├─ config_loader.py              
│  │  ├─ model_loader.py               
│  │  └─ __init__.py                   
│  ├─ workflows                        
│  │  ├─ interview_workflow.py         
│  │  ├─ report_generator_workflow.py  
│  │  ├─ xxx.py                        
│  │  └─ __init__.py                   
│  └─ __init__.py                      
├─ static                              
│  ├─ css                              
│  │  └─ styles.css                    
│  └─ js                               
│     └─ app.js                        
├─ Dockerfile                          
├─ get_lib_versions.py                 
├─ main.py                             
├─ pyproject.toml                      
├─ README.md                           
├─ requirements.txt                    
├─ setup.py                            
└─ users.db                            
             

```

## 🚀 Quick Start

### 1. Environment Setup

```bash
# Clone the repository
git clone https://github.com/suman520-git/automated-research-report-generation.git
cd automated-research-report-generation

# Create virtual environment
conda create -p venv python==3.11 -y
conda activate venv/ 

# Install dependencies
pip install -r requirements.txt
```

### 2. Configuring the MLFLOW in the project

```bash
# commnds 
step.1  pip install  mlflow
step.2  mlflow ui

visit for mlflow ui : 127.0.0.1:5000
```

## MLFLOW UI
![image alt](https://github.com/suman520-git/automated-research-report-generation/blob/main/UI-Signup.png?raw=true)
![image alt](https://github.com/suman520-git/automated-research-report-generation/blob/main/UI-Login.png?raw=true)
![image alt](https://github.com/suman520-git/automated-research-report-generation/blob/main/UI-Generate_report.png?raw=true)
![image alt](https://github.com/suman520-git/automated-research-report-generation/blob/main/UI-Feedback.png?raw=true)
![image alt](https://github.com/suman520-git/automated-research-report-generation/blob/main/UI-Ready%20for%20download.png?raw=true)


### 3. Training ML models

```bash
# For training the models on the dataset
step.1  python -m run_pipeline

```

### 4. API Usage

```bash
# For running the application through Fastapi(command for running the ml application)
step.1  uvicorn api.main:app --reload

```
## ML Application UI
![image alt](https://github.com/suman520-git/phising-website-detection/blob/main/ML-UI.png?raw=true)



### 5.  Dockerization
```bash
# Build Docker Image
step.1 docker build -t test .

#Run Docker Container
step.2 docker run --rm -p 8000:8005 test

```

### 6. Deployment to AWS APP Runner
```bash
Repository secrets

1. AWS_ACCESS_KEY_ID = "xxxxx"
2. AWS_SECRET_ACCESS_KEY = "xxxxx"
3. AWS_REGION = "xxxxx"
4. ECR_REPO = "xxxxx"

Create ECR repo copy the URI and keep it to ECR_REPO
Create a IAM user a provide this permission: AdministratorAccess

```
###########################################################################################

