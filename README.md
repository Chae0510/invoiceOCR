# Invoice OCR Processing with Google Cloud Vision and OpenAI
This project demonstrates how to use Google Cloud Vision API and OpenAI API to extract text from invoice documents and organize the information into a JSON format.

## Code Description - FrontEnd
[FrontEnd README](https://github.com/PeopleSpace-Invoice-OCR/Invoice-FE/blob/main/README.md)

## Code Description - BackEnd
#### 1. api.py
1.1. **/api/login**

The '/api/login' endpoint handles login requests. When the user enters the ID/PW and sends it to the server, it uses RESTapi provided by ERPNext to authenticate the user.

1.2. **/api/invoice**

This is an api that extracts text from the invoice image taken over from the front-end using the OCR module. Returns the extracted text in json format.

#### 2. invoiceOcr.py
2.0. **Invoice Example**
<img width="678" alt="image" src="https://github.com/PeopleSpace-Invoice-OCR/Invoice-BE/assets/85086390/0c736f3b-081a-4097-8151-2421ee8dc910">

2.1. **OCR Text Extraction**
   - Utilize Google Cloud Vision API to extract text from images.
   - OCR technology recognizes text within the image and converts it to character data.
<img width="594" alt="image" src="https://github.com/PeopleSpace-Invoice-OCR/Invoice-BE/assets/85086390/04ab8b37-c047-4f05-97b5-fb9ff6268f43">


2.2. **Information Extraction via OpenAI API**
   - Write prompts for the OpenAI API based on the text obtained from OCR results.
   - Example prompt: "Please find the company name, address, telephone number, order number, order date, and total amount in the following text."

2.3. **OpenAI API Call**
   - Invoke the OpenAI API using Python code and send the written prompts.
   - Extract the required information from the API response.

2.4. **Mapping Extracted Information to JSON**
   - Analyze the response received from the API to identify necessary information.
   - Map identified information to a predefined JSON structure.
<img width="501" alt="image" src="https://github.com/PeopleSpace-Invoice-OCR/Invoice-BE/assets/85086390/a26bf640-34a3-4d3e-b71a-0b27c935c02c">

## How to Use
### Before You Start

Before using this code, you need to obtain API keys from Google Cloud and OpenAI, as these keys will be used in the code.

1. [OpenAI](https://platform.openai.com/api-keys)

> #### Step 1: Create an OpenAI Account
>1. Visit the OpenAI website at [https://openai.com/](https://openai.com/).
>2. Click on the 'Sign Up' button to create a new account. If you already have an account, click on 'Log In' instead.
>3. Follow the on-screen instructions to complete the sign-up process.

>#### Step 2: Access the API Section
>1. Once logged in, navigate to the API section of the website, which can usually be found in the dashboard or under a section labeled 'API' or 'Developers'.
>2. Here, you will find information about the different APIs OpenAI offers and how to use them.

>#### Step 3: Generate an API Key
>1. Look for a button or link that says 'Generate API Key', 'Create New Key', or something simila
>2. Click on this link or button to create a new API key. You may be prompted to provide additional information or confirm your account details.
>3. Once the key is generated, make sure to copy it and store it in a secure location. You will need this key to authenticate your applications with OpenAI's API.

>#### Step 4: Using Your OpenAI API Key
>1. With your API key, you can now access OpenAI's API services. To use your key, include it in the HTTP header of your API requests as follows:

2. [gcloud](https://cloud.google.com/iam/docs/keys-create-delete?hl=ko#creating)

### How to Set Up

Follow these steps to set up and run the project.

 1. **Clone the Project** 

Clone the project from GitHub:

```bash
git clone https://github.com/PeopleSpace-Invoice-OCR/Invoice-BE.git
cd Invoice-BE
```

 2. **Install Required Packages**

Use the following command to install the necessary Python packages:

```bash
pip install fastapi
pip install requests
pip install google-cloud-vision
pip install openai
```

3. **Set Up Google Cloud Vision API Key**

Copy the service account key (JSON file) you obtained from the Google Cloud Console to the project directory. Then, set an environment variable to specify the API key:

```bash
export GOOGLE_APPLICATION_CREDENTIALS='./your-google-cloud-key.json'
```

This command applies only to your current terminal session. You will need to reset the environment variable if you use a different session to run the code.

4. **Apply Your OpenAI API Key**

Apply the API key you obtained from the OpenAI website to the code. Open the code file and find the following section to replace `your api key` with your actual API key:

```python
api_key = 'your api key'
```

5. **Running the Script** 

Once everything is set up, run the script with the following command, providing the path to your image file as an argument:

```bash
python script_name.py path_to_your_image.jpg
```

This script extracts text from the image and uses OpenAI to convert the important information into a structured JSON format.

6. **Notes**

- This script uses the Google Cloud Vision API and OpenAI API. Be aware of potential costs depending on your usage, so monitor your API consumption.
- API keys are sensitive information. Make sure they are not disclosed publicly.


This content provides step-by-step instructions to help users easily set up and run the project. Adjust the details as necessary to fit your specific requirements.

## Overview
<img width="754" alt="image" src="https://github.com/PeopleSpace-Invoice-OCR/Invoice-BE/assets/85086390/3c1f7428-d491-4f1a-894f-4050373ad01b">

#### 1. Photo Capture: User photographs the invoice.
#### 2. OCR Text Extraction: Google Cloud Vision API extracts text from the image.
#### 3. OpenAI API Query: Call the OpenAI API with prompts to extract specific information.
#### 4. Data Extraction: Retrieve necessary information from the API response.
#### 5. JSON Mapping: Map extracted data into a predefined JSON structure.
#### 6. User Verification: User reviews the mapped data.
#### 7. Data Save: User clicks 'save', and the information is stored in the ERPNext system.
#### 8. Feedback Loop: Continuous feedback and updates through GitHub.
