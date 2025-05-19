# **Project-X: GitHub API Setup Checklist**

This checklist outlines the key information and setup steps required to enable the Ctx ChatBot application (Project-X) to interact with the cda-matrix GitHub repository via the GitHub API for persistence of the CDA, CL, and other artifacts.

## **1\. GitHub Authentication Method**

* **Decision Point:** Choose the primary authentication method for Project-X to interact with the GitHub API.  
  * \[ \] **Personal Access Token (PAT):**  
    * **Pros:** Simpler to set up for initial development and testing, especially if the repository is owned by a personal account or direct user control is desired.  
    * **Cons:** Tied to a specific user account; broader permissions might be granted than necessary if not carefully scoped; less ideal for production or team-shared applications.  
  * \[ \] **GitHub App:**  
    * **Pros:** More secure and granular permission model (can be scoped to specific repositories and specific permissions); acts as its own identity rather than a user's; better for production and automated workflows.  
    * **Cons:** More complex initial setup.  
* **Action Item:**  
  * \[ \] Discuss and decide on the preferred authentication method (PAT or GitHub App).

## **2\. If Using Personal Access Token (PAT):**

* **Information to Gather/Generate:**  
  * \[ \] **GitHub Account:** Identify the GitHub user account from which the PAT will be generated (this account must have appropriate permissions on the cda-matrix repository).  
  * \[ \] **PAT Value:** Generate a new PAT.  
    * **Note:** The token value is only shown once upon creation. It must be copied and securely stored immediately.  
  * \[ \] **PAT Description/Note:** Assign a clear, descriptive note to the PAT in GitHub (e.g., "Project-X Ctx ChatBot API Access").  
  * \[ \] **PAT Expiration:** Decide on and set an appropriate expiration policy for the PAT (e.g., 30 days, 90 days, custom, or no expiration – though finite expiration is generally recommended for security).  
  * \[ \] **PAT Scopes (Permissions):** Select the minimum necessary scopes. For our MVP, this would likely include:  
    * repo (Full control of private repositories) \- This is a broad scope. For more fine-grained control, consider:  
      * repo:status (Access commit status)  
      * repo:deployments (Access deployment status)  
      * public\_repo (Limit access to public repositories, if cda-matrix is public)  
      * **Specifically for content:**  
        * contents:read (to read CDA, CL, etc.)  
        * contents:write (to update CL, save artifacts)  
      * **If using Pull Requests for CL updates:**  
        * pull\_requests:write (to create Pull Requests)  
* **Action Items:**  
  * \[ \] Generate the PAT with the chosen scopes and expiration.  
  * \[ \] Securely store the PAT value for use in the Project-X server-side application.

## **3\. If Using a GitHub App:**

* **Information to Gather/Generate:**  
  * \[ \] **GitHub App Name:** Decide on a name for the GitHub App (e.g., "Ctx Project-X Persistor").  
  * \[ \] **GitHub Account/Organization:** Determine under which account or organization the GitHub App will be registered.  
  * \[ \] **App ID:** Obtained after registering the App.  
  * \[ \] **Installation ID:** Obtained after installing the App on the cda-matrix repository.  
  * \[ \] **Private Key:** Generate and securely download the App's private key (usually a .pem file).  
  * \[ \] **Permissions:** Configure the necessary repository permissions for the App. These would be similar to PAT scopes:  
    * **Repository Permissions:**  
      * Contents: Read & write (for CDA, CL, artifacts)  
      * Pull requests: Read & write (if using PRs for CL updates)  
      * Metadata: Read-only (often required by default)  
    * **Subscribe to Events (Optional, for future enhancements):**  
      * E.g., Push events, Pull request events, if Ctx needs to react to repository changes.  
* **Action Items:**  
  * \[ \] Register the GitHub App.  
  * \[ \] Configure its permissions.  
  * \[ \] Generate and securely store its private key.  
  * \[ \] Install the App on the cda-matrix repository and note the Installation ID.

## **4\. Repository Information:**

* **Information to Gather:**  
  * \[ \] **Repository Owner/Organization:** The username of the owner or the name of the organization that owns the cda-matrix repository.  
  * \[ \] **Repository Name:** cda-matrix (confirm if any variations).  
  * \[ \] **Default Branch Name:** The name of the primary branch from which Ctx will read the CDA and CL (e.g., main, master).  
  * \[ \] **Target Branch for CL Updates (if not default):** If CL updates (especially via PRs) should target a specific development branch before merging to default.  
  * \[ \] **Specific File Paths:**  
    * \[ \] Path to the CDA file (e.g., core/Persona-Ctx-CDA-D-053.md).  
    * \[ \] Path to the CL file (e.g., core/conceptual-lexicon.md or core/conceptual-lexicon.json).  
    * \[ \] Default path/directory for saving other artifacts (e.g., ctx\_outputs/req\_res\_summaries/).

## **5\. Workflow Decisions (for Project-X Application Logic):**

* **Decision Points:**  
  * \[ \] **CL Update Strategy:**  
    * Direct commit to a branch?  
    * Create a new branch, commit, and then create a Pull Request? (Recommended for reviewability).  
  * \[ \] **Commit Message Format:** Define a standard format for commit messages generated by Ctx (e.g., "Ctx: Update CL with new entry \[Term\]", "Ctx: Save session artifact \[filename\]").  
  * \[ \] **Error Handling:** How should Project-X handle API errors from GitHub (e.g., authentication failure, rate limits, file not found, merge conflicts if attempting direct writes)?  
  * \[ \] **Frequency/Triggers for Saving CL:**  
    * At the end of every user session?  
    * Upon explicit user command (e.g., "Ctx, persist CL")?  
    * After a certain number of CL modifications?

This checklist should help us gather all the necessary prerequisites for enabling Project-X to interact securely and effectively with your GitHub repository.