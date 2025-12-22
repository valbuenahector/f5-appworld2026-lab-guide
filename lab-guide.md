# AppWorld 2026 – Code. Secure. Repeat. Lab Guide

This lab provides a hands-on experience using modern development and security tools, focusing on a repeatable **"Code. Secure. Repeat."** workflow.

---

## Module 0 – Intro & Environment Orientation (20 minutes)

**Technologies Used:** Python, F5 Distributed Cloud (vK8s, WAAP, WAS), Terraform (`volterraedge` provider), GitLab CE with CI/CD, and VSCode Server with the Cline extension.

### TASK 1 – Verify Access

1.  **Welcome & Overview:** Instructors provide an overview of the UDF environment and a brief walkthrough of the lab workflow.
2.  **Verify Visual Studio Code Server Access (browser-based):**
    - Ensure you can access the VSCode Server interface. Password on Lab Document in Teams
    - *(Image Reference: `Appworld2026/Module0/code-server-access.png`,`Appworld2026/Module0/code-server-access-password.png`,`Appworld2026/Module0/code-server-landing.png`)*
    - NOTE: Stuendes will somtime see this pop-up. They shoudl allow
    - *(Image Reference: `Appworld2026/Module0/module1-cline-demo-app-terminal-4-chrome-popup`)*
    - Close vscode welcome file and close vscode code assistant
2.  **Gitlab Server Access (browser-based):**
    - IMAGES ARE PENDINGS
3.  **Verify F5 Distributed Cloud (F5XC) Tenant Access:**
    - Accept the invitation email to your F5 account.
    - *(Image Reference: `Appworld2026/Module0/f5xc-email-invitation.png`)*
    - Accept the Terms of Service and Privacy Policy.
    - *(Image Reference: `Appworld2026/Module0/f5xc-terms.png`)*
    - Log in to the F5 Distributed Cloud Console.
    - Select your user preferences (e.g., **Super User**, **Advanced** level).
    - *(Image Reference: `Appworld2026/Module0/f5xc-superuser.png`, `Appworld2026/Module0/f5xc-user-level.png`)*
4.  **Verify Pre-created Objects:** Confirm existence of Namespaces, CEs, VSITE, and the vK8s cluster (automated).
5.  **Capture student namespace:**
    - *(Image Reference:
     `Appworld2026/Module0/f5xc-console-account-settings.png`,
     `Appworld2026/Module0/f5xc-console-account-settings-namespaces.png`, `Appworld2026/Module0/f5xc-console-account-settings-namespaces-2.png`)*
6.  ****Generate F5XC API Token:**:**
    - *(Image Reference:
     `Appworld2026/Module0/f5xc-console-account-settings-credentials.png`,
     `Appworld2026/Module0/f5xc-console-account-settings-credentials-token.png`, `Appworld2026/Module0/f5xc-console-account-settings-credentials-token-2.png`)*

---

### TASK 2 – Configure Cline Extension and GitLab Environment

1.  **Configure VSCode Cline Extension:**
    - Make sure you in the Cline extension view with Vscode 
    - *(Image Reference: `Appworld2026/Module0/module1-cline-icon.png`)*
    - Choose **"Bring my own API key"** for the Cline extension.
    - *(Image Reference: `Appworld2026/Module0/cline-config-1.png`)*
    - Configure the provider:
        - **API Provider:** GCP Vertex AI
        - **Model:** `gemini-2.5-flash`
    - *(Image Reference: `Appworld2026/Module0/cline-config-2.png`)*
    - Close Cline popup:
    - *(Image Reference: `Appworld2026/Module0/cline-config-3.png`)*
    - Enter Welcome prompt:

    ```text
    Hi Gemini!! Welcome to AppWorld 2026!! We are going to have fun vibe coding !!
    ```

    - *(Image Reference: `Appworld2026/Module0/gemini-hello-prompt.png`)*
    - Note Gemini's response. This ensures VSCode is talking to Gemini.
    - *(Image Reference: `Appworld2026/Module0/gemini-hello-response.png`)*

2.  **Configure GitLab:** Configure your GitLab environment with the F5XC API token and verify connectivity.
    - IMAGES ARE PENDING

---

## Module 1 – AI-Generated Vulnerable App (Demo Only)

This module is a demonstration of **AI-assisted "Vibe Coding"** and how it can introduce typical flaws and vulnerabilities.

1.  **Explore Cline Extension:** Open the Cline chat in VSCode Server and initiate a new task.
    - *(Image Reference: `Appworld2026/Module1/module1-cline-start-new-task.png`)*
2.  **Generate App Request:** Use the prompt below to request a simple Flask web application. Make sure the the Cline toggle is set to "Plan":

    ```text
    Create a simple Flask web application for demo purposes.

    Requirements:
    - Use Python Flask.
    - No authentication, no database, no external APIs.
    - Single Flask app file named app.py.
    - Use Jinja2 templates.
    - Create a modern, clean UI using Tailwind CSS via CDN (do NOT install Tailwind locally).
    - App should be visually appealing but simple.
    - Do not use the echo or open commands.

    App behavior:
    - Home page (/) with:
      - A centered hero section with a title and short description.
      - A navigation bar at the top.
      - 3 feature cards laid out in a responsive grid.
    - An /about page with a short paragraph explaining this is a demo app.
    - Use base.html for layout and extend it in other templates.

    Technical requirements:
    - Flask app must bind to 0.0.0.0.
    - App must be runnable with: flask run --host=0.0.0.0 --port=5000
    - Do not include Docker, Kubernetes, CI/CD, or security features.
    - Keep the code readable and well-commented.

    Deliverables:
    - app.py
    - templates/base.html
    - templates/index.html
    - templates/about.html

    After generating the files, explain how to run the app using flask run.
    ``` 
    - *(Image Reference: `Appworld2026/Module1/module1-cline-demo-app-plan.png`)*
3.  **Review AI Plan (Plan Mode):** The AI will outline its plan to create the necessary files.
    - *(Image Reference: `Appworld2026/Module1/module1-cline-demo-app-plan-response.png`)*
4.  **Generate Code (Act Mode):** Approve the plan to let the AI generate the files.
    - After Cline finishes coding each files it will ask the student save the file before continuing to the next file 
    - *(Image Reference: `Appworld2026/Module1/module1-cline-demo-app-act.png`,`Appworld2026/Module1/module1-cline-demo-app-act-2.png`)*
5.  **Review Generated Files:** Check the created files, including `app.py`, which sets up the `/` and `/about` routes.

    - *(Image Reference: `Appworld2026/Module1/module1-cline-demo-app-act-3-task-completed`)*

6.  **Run the Application:** Install Flask (if necessary) and execute the run command in the terminal.
    - **Command:** ```bash
    flask run --host=0.0.0.0 --port=5000
    ```
    - *(Image Reference: `Appworld2026/Module1/module1-cline-demo-app-act-3-flask-command.png`)*
7.  **Verify Running Application:** Confirm the server starts and is running on the specified host/port.
    - *(Image Reference: `Appworld2026/Module1/module1-cline-demo-app-terminal-4-flask-running.png`)*
8.  **Access the App:** Access the application:

    * **Option 1:** Access in your web browser launching from VSCode. After running the flask command, you should see a popup from VSCode. Click **Open** and the app will open in your browser.
        - *(Image Reference: `Appworld2026/Module1/module1-cline-demo-app-terminal-4-vscode-access.png`)* 
    * **Option 2:** Access the app using the Firefox container running on the Jumphost.
        - *(Image Reference: `Appworld2026/Module1/module1-cline-demo-app-terminal-4-firefox.png`)*
        - *(Image Reference: `Appworld2026/Module1/module1-cline-demo-app-terminal-4-firefox-address.png`)*

9.  **Stop Flask and Clean Up:** - Press `Ctrl+C` in the terminal to stop the server.
    - *(Image Reference: `Appworld2026/Module1/module1-cline-demo-app-terminal-ctrlc-close.png`)*
    - *(Image Reference: `Appworld2026/Module1/module1-cline-demo-app-cleanup.png`)*