## NAME  
Glyph — Automated generator for Unix/Linux man page–style documentation from script files

## SYNOPSIS  
**Web-based usage:**  
&nbsp;&nbsp;&nbsp;&nbsp;Open the URL for your n8n-hosted form  
&nbsp;&nbsp;&nbsp;&nbsp;Fill out the "Generate Documentation with Glyph" form:  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Script Name: `<name>`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Give a brief overview of your script: `<overview>`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Provide script file(s): `<upload file>`  
&nbsp;&nbsp;&nbsp;&nbsp;Submit the form  
&nbsp;&nbsp;&nbsp;&nbsp;Download the generated documentation as a `.txt` file  

## DESCRIPTION  
Glyph is an automated documentation generator that produces basic Unix/Linux man page–style  
documentation for scripts. It is accessed via a web form hosted via n8n. Users provide the  
script name, a brief overview, and upload the script file. Glyph processes the submission by  
extracting the script content, analyzing comments, docstrings, and structure, and then  
generating documentation in standard man page sections: **NAME**, **SYNOPSIS**, **DESCRIPTION**,  
**OPTIONS**, **EXAMPLES**, and **SEE ALSO**. The output is delivered as a downloadable `.txt` file.  

The workflow is implemented as an n8n automation with the following logical steps:  
&nbsp;&nbsp;&nbsp;&nbsp;1. Initial Web Form Submission: Collects script name, overview, and file upload.  
&nbsp;&nbsp;&nbsp;&nbsp;2. Extract contents of uploaded script: Reads the uploaded script file as text for processing.  
&nbsp;&nbsp;&nbsp;&nbsp;3. GPT 4.1 Produces documentation: Uses GPT-4.1 to analyze the overview and script,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;generating man page–style documentation.  
&nbsp;&nbsp;&nbsp;&nbsp;4. Documentation converted to txt file: Converts the generated documentation to a `.txt` file.  
&nbsp;&nbsp;&nbsp;&nbsp;5. Form ends with file download: Presents a completion screen and provides the `.txt` file  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;for download.  

All user input and script content are processed securely within the workflow. The generated  
documentation includes all relevant details, options, and configuration keys present in the script.

## OPTIONS  

**Web Form Fields:**  
&nbsp;&nbsp;&nbsp;&nbsp;**Script Name**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Required field.  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The name of the script to be documented.  

&nbsp;&nbsp;&nbsp;&nbsp;**Give a brief overview of your script.**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Required field.  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;A short description or summary of the script’s purpose.  

&nbsp;&nbsp;&nbsp;&nbsp;**Provide script file(s)**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Field type: file.  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Multiple files: false (only one file can be uploaded).  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The script file to be documented.  

**Internal Workflow Parameters:**  
&nbsp;&nbsp;&nbsp;&nbsp;**formTitle**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Value: `"Generate Documentation with Glyph"`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The title displayed on the web form.  

&nbsp;&nbsp;&nbsp;&nbsp;**webhookId**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Value: `"****-****-****-****-************"`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The unique identifier for the form trigger webhook.  

&nbsp;&nbsp;&nbsp;&nbsp;**modelId**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Value: `"gpt-4.1"`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The language model used for documentation generation.  

&nbsp;&nbsp;&nbsp;&nbsp;**temperature**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Value: `0.2`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Controls the randomness of the language model output.  

&nbsp;&nbsp;&nbsp;&nbsp;**topP**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Value: `0.2`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Controls the diversity of the language model output.  

&nbsp;&nbsp;&nbsp;&nbsp;**fileName**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Value: Script Name (as provided by the user)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The name of the generated documentation file.  

&nbsp;&nbsp;&nbsp;&nbsp;**completionTitle**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Value: `"Download Documentation from Glyph"`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The title displayed on the completion screen.  

&nbsp;&nbsp;&nbsp;&nbsp;**completionMessage**  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Value: `"Your documentation is complete!"`  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The message displayed when the documentation is ready for download.

## EXAMPLES  

**Typical usage:**  
&nbsp;&nbsp;&nbsp;&nbsp;1. Navigate to your n8n webform URL  
&nbsp;&nbsp;&nbsp;&nbsp;2. Enter `"my_script.sh"` as Script Name.  
&nbsp;&nbsp;&nbsp;&nbsp;3. Enter `"A shell script to automate backups."` as the overview.  
&nbsp;&nbsp;&nbsp;&nbsp;4. Upload `"my_script.sh"`  
&nbsp;&nbsp;&nbsp;&nbsp;5. Submit the form  
&nbsp;&nbsp;&nbsp;&nbsp;6. Download the generated `"my_script.sh.txt"` documentation file

## SEE ALSO  
- n8n workflow automation  
- Unix man page documentation standards  
- OpenAI GPT-4.1 language model
