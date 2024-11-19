# MicroServiceTeammate

==How to programmatically request data from the microservice==

To request data from the microservice, make an HTTP POST call to the /validate_csv endpoint. The request should specify the path to the CSV file that requires validation.

--Endpoint--

URL is http://127.0.0.1:5000/validate_csv.

Method: POST.

Content-Type: application/json.

Request Body: A JSON object with the key file_path and the value as the path of the CSV file.

--Example Request--
import requests

# Define the URL and the payload
url = 'http://127.0.0.1:5000/validate_csv'
payload = {
    "file_path": "test.csv"
}

# Make the POST request
response = requests.post(url, json=payload)

# Print the response
print(response.json())

--Instructions for Requesting--

Install the required Python libraries using pip:

pip install requests

Save your CSV file to the desired location and adjust the file path in the payload.

Use the example script above to send a request to the microservice.

==How to Programmatically Receive Data from the Microservice==

--Response Format--

Valid Response: The response will include two keys:

valid (boolean): Indicates whether the CSV file passed validation.

issues (list): Contains any issues or missing data in the CSV file.

--Example Response--

{
    "valid": true,
    "issues": []
}

If there are issues, the response might look like:

{
    "valid": false,
    "issues": [
        "Row 3 has incorrect number of columns.",
        "Missing value in column 'price' at row 5."
    ]
}

--Instructions for Receiving Data--

Use the requests library to send the POST request as described above.

The response object will have a .json() method that can be used to parse the response data.

Handle the data as required, for example, logging issues or taking corrective actions based on the validation results.

UML DIAGRAM:
![image](https://github.com/user-attachments/assets/06b2355d-c315-4b42-a7bb-edb779f7015d)
