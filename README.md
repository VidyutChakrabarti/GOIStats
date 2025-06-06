## Study on Household Consumption and Inflation data
Deriving inferences from datasets sourced from the national data archive.  
### Repository Structure
![repo structure diagram](assets/repostructure.png)

## Current Datasets   

1. **Household Consumption Dataset**  
   - [Dataset Link](https://microdata.gov.in/NADA/index.php/catalog/237)
   - We have taken 2023-24 data for our analysis.  
   - Can be accessed through [Nesstar Publisher](https://www.ihsn.org/software/ddi-metadata-editor)  

2. **Consumer Price Index and Inflation Data**  
   - [Dataset Link](https://esankhyiki.mospi.gov.in/macroindicators?product=cpi)  

***To get the cleaned dataset:*** Download the S3-Data and explore it.

<br/>

You can access the cleaning script from here: [![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1K5T8ZZ_sY3dv31pMmmQPrZLA40inmn_P?usp=sharing)

Youtube video: [Link](https://www.youtube.com/watch?v=qLz7aWlV5A0)

### Pipeline overview:
![pipeline diagram](assets/sysdig.png)

### Our final database schema looks like this: 
![Schema diagram](assets/psqlschema.png)

#### In order to deploy on AWS: 
1. Create terraform.tfvars with appropriate access keys to your account(must have a proper IAM role)
2. First deploy GOIStats/bootstrap with the following commands: 
```bash
terraform init
```

If credentials problem comes up then configure your environment using: 
```bash
aws configure
```

Finally use: 
```bash
terraform plan
```
```bash
terraform apply -auto-approve
```

- Upload the psycopg2-layer.zip as a layer in the Lambda function, this packaged layer has been prepared in AWS-Linux OS. (using a zipped package from Windows gives an error.)

**Note: Additional charges may apply if large datasets are transferred within the vpc using lambda, we avoided using AWS Glue due to cost constraints.**

### PowerBI dashboard: 
![powerbi dashboard](assets/vis.png)



