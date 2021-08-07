### Command Line

Study guide for Google Cloud Engineer Certification

##### Projects

```bash
# Set up the environment variable
export GOOGLE_APPLICATION_CREDENTIALS="./service-account.json"
```

```bash
# List projects
gcloud compute instances list

# Sign in account
gcloud auth login

# Set up project
gcloud config set project <project_id>

# Set up project zone
gcloud config set compute/zone us-central1-f

# Info about the project
gcloud info

# Returns id project
gcloud config get-value core/project
```

##### Service Account

```bash
# Create service account
gcloud iam service-accounts create <service_account_name> --description=<description> --display-name=<display_name>

# Create service account keys
gcloud iam service-accounts keys create ~/key.json --iam-account <service_account_name>@<project_id>.iam.gserviceaccount.com

# Set up access control
gcloud projects add-iam-policy-binding <project_id> --member "serviceAccount:<service_account_name>@<project_id>.iam.gserviceaccount.com" --role "roles/bigquery.user"

gcloud projects add-iam-policy-binding <project_id> --member "user:<e-mail>" --role "roles/editor"

gcloud projects add-iam-policy-binding <project_id> --member "group:<e-mail>" --role "roles/editor"

# View service account roles
gcloud projects get-iam-policy <project_id>

# Export policies
gcloud projects get-iam-policy <project_id> > /tmp/policy.yaml
```

##### APIs

```bash
# List services 
gcloud services list

# Enable google api
# Ex.: gcloud services enable <service>.googleapis.com
gcloud services enable cloudfunctions.googleapis.com \
    cloudbuild.googleapis.com \
    dataproc.googleapis.com \
    compute.googleapis.com \
    pubsub.googleapis.com \
    storage-component.googleapis.com \
    bigquery.googleapis.com \
    bigquerystorage.googleapis.com

# Disable google api
gcloud services disable pubsub.googleapis.com

```

##### Cloud Compute

```bash

```

##### Cloud Storage

```bash
# Create a bucket
gsutil mb <storage_name> -p <project_id> -c <storage_class> -l <region>

# Copy file from local to storage
gsutil cp <local_file> gs://<bucket_name>

# Copy file from storage to local
gsutil cp gs://<bucket_name> <local_file>
```

##### Bigquery

```bash
# Show Schema
bq show bq show bigquery-public-data:samples.shakespeare

# Help command
bq help query

# List any existing datasets
bq ls

# List any existing datasets in a project
bq ls <project_id>:

# Create a new dataset
bq mk <dataset_name>

# Run a query
bq query --use_legacy_sql=false \
'
SELECT 
    word
FROM
   `bigquery-public-data`.samples.shakespeare
WHERE
   word LIKE "%raisin%"
'

```

##### Pub/Sub

```bash

```

##### Dataproc

```bash
gcloud dataproc clusters create ${CLUSTER_NAME} \
    --region=${REGION} \
    --zone=${ZONE} \
    --image-version=2.0 \
    --scopes=default,sql-admin \
    --master-machine-type=${MASTER_MACHINE_TYPE} \
    --master-boot-disk-size=${MASTER_BOOT_DISK} \
    --num-workers=${NUM_WORKERS} \
    --worker-machine-type=${WORKER_MACHINE_TYPE} \
    --worker-boot-disk-size=${WORKER_BOOT_DISK} \
    --bucket=${BUCKET_NAME} \
    --optional-components=ANACONDA,JUPYTER \
    --enable-component-gateway \
    --tags=lab \
    --initialization-actions gs://dataproc-initialization-actions/python/pip-install.sh \
    --metadata 'PIP_PACKAGES=google-cloud-storage'
    
    
gcloud dataproc jobs submit pyspark \
gs://${BUCKET_NAME}/<script.py> --cluster=${CLUSTER_NAME} --region=${REGION}
```

##### Cloud Functions

```bash

```

##### 

```bash

```
