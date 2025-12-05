## 📘 Contributing to the Matter Handbook

Welcome! Thank you for helping us improve the Matter Handbook.

> [!NOTE]
> **Have a question?** Start a [Discussion](https://github.com/project-chip/matter-handbook/discussions).
> 
> **Ready to work?** Open an [Issue](https://github.com/project-chip/matter-handbook/issues/new/choose) or submit a [Pull Request](https://github.com/project-chip/matter-handbook/compare).

---

### ⚙️ How We Work

To keep this handbook accurate and high-quality, we follow a specific flow:

1.  **Everything is a Pull Request (PR):** Whether it is a typo fix or a new chapter, it goes through a PR. We do not push directly to the `main` branch.
2.  **Automation First:** We use bots to check spelling and formatting automatically.
3.  **Label-Driven:** The label you choose determines who needs to approve your work.
4.  **Auto-Merge:** Once all approvals and checks pass, the system merges your work automatically. No manual "merge button" required.

---

### 🔀 Git Workflow

Depending on how often you contribute, choose the right setup:

| You are... | Where to work | Setup Command | After Merge |
|:---|:---|:---|:---|
| **First-timer / Infrequent** | A **Fork** (your own copy) | Click "Fork" on GitHub, then clone your fork. | You can delete the branch in your fork. |
| **Frequent Contributor** | A **Branch** in this repo | `git switch -c feature-name` | Branch is auto-deleted by the system. |

---

### 🚀 Step-by-Step Guide

Follow this standard workflow to ensure your contribution moves smoothly from idea to merged code.

#### 1. Create Your Workspace (Fork & Clone)
First, create your own copy of the repository so you can work freely without affecting the main handbook.
*   **Fork:** Click the **Fork** button in the top-right corner of this page.
*   **Clone:** Download your fork to your machine.
    *   `git clone https://github.com/<your-username>/handbook.git`

#### 2. Isolate Your Change (Branch)
Always work on a specific branch, never directly on `main`. This keeps your changes organized.
*   **Command:** `git switch -c <descriptive-name>`
*   **Example:** `git switch -c fix-typo-intro` or `git switch -c add-certification-guide`

#### 3. Edit and Preview
We use **Retype** to build this handbook. The best way to work is using the **Dev Container** in VS Code, which installs all tools for you automatically.
*   **Setup:** Open the project folder in VS Code. When prompted (or via the Command Palette), select **"Reopen in Container"**.
*   **Run Preview:** Open the integrated terminal and follow the [Retype Getting Started guide](https://retype.com/guides/getting-started/) (typically running `retype watch`).
*   **View:** Click the `localhost` link that appears in the terminal to browse the fully functional website on your computer.

#### 4. Save Your Work (Commit)
When you are happy with the preview, save a snapshot of your work:
*   **Stage files:** `git add .`
*   **Save snapshot:** `git commit -m "Brief description of change"`

#### 5. Upload (Push)
Send your changes from your machine up to your Fork on GitHub.
*   **Command:** `git push -u origin <descriptive-name>`

#### 6. Open the Pull Request (PR)
1.  Go to the main repository page.
2.  Click the yellow **Compare & pull request** banner.
3.  **Crucial Step:** Select the correct **Label** (see table below) to ensure the right people review it.

---

### 🏷️ Choosing the Right Label

Labels are critical. They tell our automation system how to handle your request.

| What are you changing? | Label to use | Who reviews it? |
|:---|:---|:---|
| **Wording / Typos / Formatting** (Meaning stays the same) | `editorial` | Any Maintainer |
| **Content / Meaning** (e.g., changing rules, adding guides) | Domain Label (e.g., `certification`, `transport`) | Maintainer + Subject Matter Expert (SME) |
| **System / CI / Infra** | `tooling` | Maintainer |
| **Work in Progress** (Not ready yet) | `do not merge` | *Merge is blocked* |

**Important Rules:**
*   If your change affects the *meaning* of the text, you **must** use a Domain label. Do not use `editorial` to bypass an expert review.
*   If a domain label is present, an external "SME Approval" check will appear to ensure technical accuracy.

---

### ✅ When Will My PR Merge?

The system will automatically merge your PR when **all** of these are true:

*   [ ] A Maintainer has approved.
*   [ ] If a Domain Label is used: The SME has approved.
*   [ ] **Vale** (our spell-checker) is green/passing.
*   [ ] All review comments are resolved.
*   [ ] The PR is not in "Draft" mode.
*   [ ] The `do not merge` label is removed.

---

### 👥 Roles and Responsibilities

| Role | What they do |
|:---|:---|
| **Author** (You) | Writes content, applies correct labels, fixes errors found by bots. |
| **Maintainer** | Checks for structure, risk, and formatting. |
| **SME** | Experts who verify the technical accuracy of the content. |

---

### 🤝 Review Etiquette

*   **One thing at a time:** Don't force-push massive changes while people are actively reviewing.
*   **Stay aligned:** Only resolve a conversation thread if the issue is actually fixed.
*   **Be patient:** If you are blocked for more than 5 business days, mention `@project-chip/handbook-maintainers`.
