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
        ==============================================
        Create a simple Flask web application for demo purposes (Module 1 – AppWorld 2026 vibe-coding demo).

        High-level goal:
        - A small, polished “conference-style” site inspired by AppWorld 2026 themes (apps, APIs, AI, hands-on learning).
        - IMPORTANT: Do NOT copy text verbatim from any website. Paraphrase into original wording.

        Requirements:
        - Use Python Flask.
        - No authentication, no database, no external APIs.
        - Single Flask app file named app.py.
        - Use Jinja2 templates.
        - Create a modern, clean UI using Tailwind CSS via CDN (do NOT install Tailwind locally).
        - App should be visually appealing but simple.
        - Do not use the echo or open commands.

        Pages / behavior:
        1) Home page (/)
        - A top navigation bar with links: Home, Agenda, About.
        - A centered hero section:
        - Title: “AppWorld 2026 – Code. Secure. Repeat.”
        - Subtitle: A short, original (paraphrased) blurb about learning to build, deliver, and protect apps/APIs/AI with hands-on labs.
        - A primary CTA button linking to /agenda.
        - 3 feature cards in a responsive grid (each with title + 2–3 bullet points):
        - “Build Faster” (AI-assisted dev + CI/CD vibe, phrased generically)
        - “Secure by Design” (WAAP, API security, bot defense themes, phrased generically)
        - “Repeatable Workflow” (“Code. Secure. Repeat.” loop, phrased generically)
        - A small “Highlights” strip below the cards with 3 quick stats (static placeholders):
        - “3 Modules”, “Hands-on Demos”, “WAAP + API Security”

        2) Agenda page (/agenda)
        - Show a simple agenda with 3 time blocks (static, fake times are OK):
        - “Module 0 – Orientation”
        - “Module 1 – Vibe Coding Demo”
        - “Module 2/3 – Deploy + API Discovery”
        - Each agenda item should have:
        - Title
        - 1–2 line description (original phrasing)
        - A “Track” badge (e.g., DevSecOps, App Delivery, API Security)
        - Add a tiny bit of interactivity:
        - Support a query string filter like /agenda?track=API
        - If track is provided, filter agenda items server-side and show “Filtered by: …”
        - Provide 3 filter links/buttons at top: All, DevSecOps, API, Delivery.

        3) About page (/about)
        - A short paragraph explaining:
        - This is a demo-only app for a lab.
        - It intentionally stays simple (no auth/db).
        - It exists to demonstrate AI-generated code + UI scaffolding.
        - Add a small callout panel: “Lab note: This demo is not the production app used in later modules.”

        UI / layout:
        - Use templates/base.html for layout (nav + footer).
        - Use templates/index.html, templates/agenda.html, templates/about.html extending base.
        - Add a footer with small text: “Demo app for AppWorld 2026 lab – Code. Secure. Repeat.”

        Technical requirements:
        - Flask app must bind to 0.0.0.0.
        - App must be runnable with: flask run --host=0.0.0.0 --port=5000
        - Keep the code readable and well-commented.
        - Do not include Docker, Kubernetes, CI/CD, or security features.

        Deliverables:
        - app.py
        - templates/base.html
        - templates/index.html
        - templates/agenda.html
        - templates/about.html

        After generating the files, explain how to run the app using flask run.
        ==============================================




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