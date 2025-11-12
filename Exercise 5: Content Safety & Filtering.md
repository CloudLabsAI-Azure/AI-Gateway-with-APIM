# Exercise 5: Content Safety & Filtering 

### Estimated Duration: 60 Minutes

## Lab Overview

Objective: Implement content safety measures to screen user inputs and AI outputs, ensuring compliance and safe interactions. 

## Lab Objectives

- Task 1: Review content safety capabilities and configuration in AI Foundry

- Task 2: Specify content filters at request time using headers

- Task 3: Apply content safety enforcement rules in API Management 

## Task 1: Review content safety capabilities and configuration in AI Foundry

**Azure AI Content Safety** helps detect and prevent harmful user-generated and AI-generated content in applications and services. Its features ensure that text, images, and other media align with your organization’s content safety guidelines.

* **Azure AI Content Safety** offers a suite of tools for monitoring and moderating content in real time:

  * **Text moderation:** Detects and filters harmful or unsafe language in text, including hate speech, violence, or explicit content.
  * **Image moderation:** Analyzes images to identify and block visual content that may be inappropriate or offensive.
  * **Multimodal content analysis:** Evaluates combined content types (such as text and images) to provide a more complete view of potential risks.
  * **Groundedness detection:** Ensures that AI-generated text is factually accurate and supported by trusted source materials.
  * **Prompt shields:** Detects and mitigates prompt injection or document-based attacks that attempt to manipulate large language models (LLMs).
  * **Protected material detection:** Identifies and blocks outputs that may contain copyrighted or third-party protected text, such as song lyrics, recipes, or articles.

These AI-powered features help organizations detect risks, prevent the spread of harmful or misleading content, and maintain a safe, trustworthy, and inclusive environment for their users.


1. Open the Azure Portal in the browser and sign in with the credentials provided in the **Environment** tab.

1. Click on the **Resource groups** from the homepage.

   ![](./media/e2t1-rg(1).png)

1. Under the **Resource groups** blade, select **Q2a-APIM-RG-<inject key="DeploymentID" enableCopy="false"/>**.

   ![](./media/rg-(1).png)

1. Select the **foundry1-<inject key="DeploymentID" enableCopy="false"/>**.

    ![](./media/e5t1p1.png)

1. Now click on the **Go to Azure AI Foundry portal**.

    ![](./media/e5t1p2.png)

1. From the left navigation pane on the Azure AI Foundry portal, select **Guardrails+controls**.

    ![](./media/e5t1p3.png)

1. Click on **Try it out** under Guardrailsand controls.

    ![](./media/e5t1p4.png)

### Task 1.1: Text Moderation

1. Click **Try it out** in the **Moderate text content** tool, located under the **Filter text content** section.

    ![](./media/e5t1p5.png)

1. Scroll down to the **Test** section, and paste the prompt **(1)** given below, and click on **Run test (2)**.

    ```
    I recently used the PowerBurner Camping Stove on my camping trip, and I must say, it was fantastic! It was easy to use, and the heat control was impressive. Great product!
    ```

    ![](./media/e5t1p6.png)

1. To view the results, scroll down to the **View Results** section. As shown, the prompt above is allowed.

    ![](./media/e5t1p7.png)

1. You can also try different prompts and adjust the threshold level to **Low**, **Medium**, or **High** from the **Configure Filters** section located next to the **Test** section.

1. Similarly, you can try out the other sample prompts provided in this section to explore how the model detects different types of content. For example, **“Violent content with misspelling”** includes harmful language with spelling errors to test how well the model recognizes unsafe text despite typos. **“Multiple risk categories in one sentence”** combines various forms of risky content in a single input to assess how the model handles complex scenarios. **“Multiple languages in one sentence”** mixes English with another language to evaluate multilingual content detection. Try each of these samples to observe how the system classifies and filters different kinds of content.
    
    ![](./media/e5t1p7(1).png)

### Task 1.2: Image Moderation

1. Go back to the **Guardrails + controls**, blade and then to the **Try it out** tab. Select **Moderate image content**, under **Filter image content**.

    ![](./media/e5t1p15.png)

1. In this section, you can test how the Azure AI Content Safety, Image Moderation tool evaluates different types of image content. You can either upload your own image or select one of the provided sample images to analyze. The tool detects categories such as violence, self-harm, and sexual content, and you can use the Configure filters panel to adjust sensitivity levels (Low, Medium, or High) for each category. Try running tests with various images and thresholds to observe how moderation results change based on content type and filter configuration.

    ![](./media/e5t1p16.png)

### Task 1.3: Multimodal content analysis

1. Go back to the **Guardrails + controls**, blade and then to the **Try it out** tab. Select **Moderate multimodal content**, under **Filter image content**.

    ![](./media/e5t1p17.png)

1. In this section, you can test how the **Azure AI Content Safety, Multimodal Moderation** tool analyzes both **images and text together** to detect harmful or inappropriate content. You can **upload your own image with text** or choose from the provided **sample memes** to see how different combinations are classified. The tool can identify risks such as **violence**, **self-harm**, or **hate**, even when the image or text alone may seem harmless. Use the **Configure filters** panel to adjust the sensitivity for each category (Low, Medium, or High) and observe how the moderation results change with different risk thresholds.

    ![](./media/e5t1p18.png)


### Task 1.4: Groundedness detection

1. Go back to the **Guardrails + controls**, blade and then to the **Try it out** tab. Select **Groundedness detection**, under **Filter text content**.

    ![](./media/e5t1p19.png)

1. In this section, you can test the **Groundedness Detection** capability, which checks whether AI-generated responses are **factually based on provided source information**. You can choose between **Q&A** or **Summarization** tasks, then either select a sample or enter your own **grounding source**, **prompt**, and **model-generated completion**. The tool compares the completion against the source text to detect if any part of the answer is **ungrounded or incorrect**. You can also enable options to **view reasoning** behind the detection or **see correction suggestions** for improving ungrounded content. This helps ensure that AI responses remain accurate and supported by reliable information.

    ![](./media/e5t1p20.png)

### Task 1.5: Prompt shields

1. Go back to the **Guardrails + controls**, blade and then to the **Try it out** tab. Select **Prompt shields**, under **Filter text content**.

    ![](./media/e5t1p21.png)

1. In this section, you can test the **Prompt Shields** feature, which helps detect and prevent **prompt injection or jailbreak attacks** that attempt to manipulate an AI model’s behavior. You can select from the provided samples or enter your own **user prompt** and **document content** to simulate different attack scenarios. Examples include **safe content**, **user prompt attacks**, **document-based attacks**, and **combined prompt and document attacks**. After entering or selecting your test data, you can run the test to see how the model identifies and blocks malicious or manipulative prompts. This tool helps ensure that your AI system remains secure and resistant to indirect or harmful prompt-based exploits.

    ![](./media/e5t1p22.png)

### Task 1.6: Protected material detection

1. Go back to the **Guardrails + controls**, blade and then to the **Try it out** tab. Select **Protected material detection**, under **Filter text content**.

    ![](./media/e5t1p23.png)

1. In this section, you can explore the **Protected Material Detection for Text** feature, which helps identify and protect **copyrighted or third-party text** that may appear in AI-generated content. You can choose from the provided samples, such as **Protected lyrics** or **Protected recipes**, or upload your own text to analyze. The tool checks whether the input contains material that may belong to protected sources and flags it accordingly. Use this to ensure your AI outputs remain compliant with copyright and intellectual property guidelines by avoiding the reuse of protected text content.

    ![](./media/e5t1p24.png)


https://learn.microsoft.com/en-us/training/modules/moderate-content-detect-harm-azure-ai-content-safety-studio/7-exercise-groundedness-detection

## Task 2: Specify content filters at request time using headers

1. In the AI Foundry portal, under My Assets, select **Model + endpoint**.

   ![](./media/API-gateway-image62.png)

2. Click on **+ Deploy Model (1)**, and from the dropdown, select **Deploy Base Model (2)**.

    ![](./media/API-gateway-image64.png)

3. Search for and select **GPT-35-Turbo**, then click **Confirm**.

   ![](./media/API-gateway-image63.png)

4. On **Deploy** **GPT-35-Turbo** page,   click on **customize**.

    ![](./media/API-gateway-image65.png)

5. Reduce the Tokens per Minute rate limit to **5K**, then click **Deploy**.

   ![](./media/API-gateway-image66.png)

6. Once deployment is completed kindly copy the **target URL** and **Key**.

    ![](./media/API-gateway-image67.png)

7. Open the VS code  from the top menu select **File > New file**.

     ![](./media/API-gateway-image68.png)

8. Paste the below code :

   ```
   import requests
   import json
    
   # 1️⃣ Set your model endpoint (correct path)
   url = <URL>
    
   # 2️⃣ Add your API key
   api_key = <api_key>
    
   # 3️⃣ Set headers for authentication and content safety
   headers = {
       "Content-Type": "application/json",
       "api-key": api_key,
       "X-Content-Safety-Level": "high",
       "X-Block-Unsafe": "true",
       "X-Content-Categories": "violence,hate,sensitive"
   }
    
   # 4️⃣ Create a test prompt
   data = {
       "model": "gpt-35-turbo",
       "messages": [
           {"role": "system", "content": "You are a helpful assistant."},
           {"role": "user", "content": "Write a story about a dragon."}
       ]
   }
    
   # 5️⃣ Send POST request
   response = requests.post(url, headers=headers, json=data)
    
   # 6️⃣ Print response
   try:
       result = response.json()
       print(json.dumps(result, indent=2))
   except json.JSONDecodeError:
       print("Error decoding response:", response.text)
   ```

9. Kindly replace the URL and API key with the values you copied in the earlier step.

10. Please review the code and pay attention to how we add the headers. These headers (X-Content-Safety-Level, X-Block-Unsafe, and X-Content-Categories) are used to specify content filters at the request time

11. Now press **Ctrl + S** to save the file, and navigate to **C:/labfiles/AI-Gateway/lab** to save the file as **ai_request** under the **labs** folder.

12. Back in VS Code, select the **ai_request.py** file, right-click, and select **Open Integrated Terminal**.

13. Install the requests library (needed to make HTTP requests to the Azure OpenAI endpoint). Run these commands one by one:

    ```
    pip install requests
    python -m pip install requests
    py -m pip install requests
    pip show requests

    ```

    **>Note:** The first three commands try different ways of installing the library depending on your Python environment.
    **>Note:** The last command (pip show requests) confirms that the library is installed.
    
14. Run the script to test the request:

     ```
     python ai_request.py
     ```   

15. Check the results printed in the console.

16. Understand the content filtering headers

    - In the script, the following headers are added:

        headers = {
            "Content-Type": "application/json",
            "api-key": api_key,
            "X-Content-Safety-Level": "high",
            "X-Block-Unsafe": "true",
            "X-Content-Categories": "violence,hate,sensitive"
        }


   - X-Content-Safety-Level → Controls how strict content safety checks are.

   - X-Block-Unsafe → Blocks any unsafe outputs automatically.

   - X-Content-Categories → Specifies which types of content to filter (e.g., violence, hate, sensitive).

   - These headers apply content filters at the request time, ensuring any output from the AI is checked for safety before it’s returned.

   - You can modify the test prompt or settings in the script if you want to try different inputs or content safety filters.

## Task 3: Apply content safety enforcement rules in API Management

In this task, you will configure and validate the Content Safety policy in the AI Gateway environment using Visual Studio Code and Azure API Management (APIM). You will initialize environment variables, deploy resources using Bicep, and test how the Content Safety service filters unsafe prompts before reaching the backend model.

1. In Visual Studio Code, expand **lab (1)** folder and select **content-safety (2)**, and finally click on **content-safety.ipynb (3)**.

    ![](./media/e5t3p1.png)

1. Once the notebook opens, take a few minutes to review the sections and understand the sequence of steps, initialization, deployment, and testing.

1. Scroll down to **Initialize notebook variables** cell and enter the following details:

   - resource_group_name: **Q2a-APIM-RG-<inject key="DeploymentID" enableCopy="false"/>**

   - aiservices_config: **foundry4-<inject key="DeploymentID" enableCopy="false"/>**

   - apim_name: **apim-<inject key="DeploymentID" enableCopy="false"/>**

   >**Note:** Ensure that the correct name is entered in the respective section section.

1. Run the cell **Initialize notebook variables**. This cell imports necessary Python utilities and environment setup scripts. Configures resource names using your Azure subscription ID. Sets region, AI Foundry configuration, model details, and deployment parameters.

    ![](./media/initvar-e5t3.png)

    >**Note:** Ensure that the correct name is entered in each respective section.

1. Next, scroll down to **Verify the Azure CLI and the connected Azure subscription** section. **Run** the cell to validate Azure CLI installation. This confirms that you are signed into the correct Azure account, display details like User Email, Tenant ID, and Subscription ID and ensures the deployment will occur in the intended Azure environment.

    ![](./media/ver-e5t3.png)

1. Next, go to **Create deployment using 🦾 Bicep** and **Run** the cell to automatically deploy all required resources, including Azure API Management, Azure OpenAI, and Azure AI Content Safety. The Bicep template ensures declarative and repeatable deployment of these services within the specified resource group.

    ![](./media/deploy-e5t3.png)

1. Once the deployment process is complete, scroll down to **Get the deployment outputs** and **Run** the cell to retrieve important information such as the APIM Service ID, Gateway URL, Content Safety Endpoint, and Subscription Key. These outputs will be used in subsequent steps to test and validate content safety behavior.

    ![](./media/outputs-e5t3.png)

1. Next, scroll to **Test the Content Safety** section and **Run** the cell to send test prompts through API Management. This verifies how the Content Safety policy filters unsafe input before sending it to the backend model. You will observe that safe prompts return responses successfully, while unsafe prompts are blocked with a 403 Forbidden status code.

    ![](./media/content-e5t3.png)

## Summary


### Conclusion


### You have successfully completed the Hands-on lab.
