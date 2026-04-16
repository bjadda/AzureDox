<div align="center">

# ⚡ AzureDox

**Opinionated. Curated. Actually useful.**

A personal handbook of the best Azure tools, docs, and links — built for people who use Azure every day, not people writing about it.

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
![Last updated](https://img.shields.io/github/last-commit/bjadda/AzureDox?label=last+updated&color=0078d4)
![PRs welcome](https://img.shields.io/badge/PRs-welcome-brightgreen)

</div>

---

## 📋 Contents

- [🚀 Start Here](#-start-here)
  - [Azure essentials](#azure-essentials)
  - [AI assistants](#ai-assistants--set-these-up-too)
  - [Installing GitHub Copilot](#installing-github-copilot)
  - [Installing Claude](#installing-claude)
- [💻 CLI & Shell](#-cli--shell)
- [🏗️ Infrastructure as Code](#️-infrastructure-as-code)
- [💰 Cost & Billing](#-cost--billing)
- [📊 Monitoring & Observability](#-monitoring--observability)
- [🔒 Security & Identity](#-security--identity)
- [🚢 DevOps & Deployment](#-devops--deployment)
- [🤖 AI & Copilot](#-ai--copilot)
- [🗄️ Data & Storage](#️-data--storage)
- [📐 Architecture & Design](#-architecture--design)
- [🔌 VS Code Extensions](#-vs-code-extensions)
- [📚 Learning & Certs](#-learning--certs)
- [🔗 Quick Reference Links](#-quick-reference-links)

> **How to read this list:**
> ⭐ = Personal best pick for the job
> 🆓 = Free tier available
> 🔵 = Microsoft official
> 🐙 = Open source

---

## 🚀 Start Here

Everything you should have set up before you write a single line of code or click a single button in the portal. Split into **Azure essentials** and **AI assistants** — both matter equally.

### Azure essentials

| Tool | What it is | Get it |
|------|-----------|--------|
| ⭐ **Azure Portal** | The main web UI for everything | [portal.azure.com](https://portal.azure.com) |
| **Azure CLI** | The terminal — faster than the portal for most tasks | [Install guide](https://learn.microsoft.com/cli/azure/install-azure-cli) |
| **VS Code + Azure extensions** | Best editor for Azure dev work | [code.visualstudio.com](https://code.visualstudio.com) |
| **Azure Pricing Calculator** | Before you provision anything, check the cost | [azure.microsoft.com/pricing/calculator](https://azure.microsoft.com/en-us/pricing/calculator/) |
| **Azure Status** | Is something down? Check here first | [status.azure.com](https://status.azure.com) |

### AI assistants — set these up too

These are the tools that actually speed up your day-to-day work. Pick your preferred AI chat tool and install Copilot in your editor. Both are worth having.

| Tool | Best for | Get it |
|------|---------|--------|
| ⭐ **GitHub Copilot** | In-editor code completion + chat, Azure CLI help, PR summaries | [github.com/features/copilot](https://github.com/features/copilot) |
| ⭐ **Claude (Anthropic)** | Long-context reasoning, architecture decisions, drafting docs | [claude.ai](https://claude.ai) |
| **ChatGPT / GPT-4o** | General coding help, quick answers | [chatgpt.com](https://chatgpt.com) |
| **Copilot in Azure Portal** | Ask questions about your live resources | Built into portal — click ✨ |

> **Which AI for what?**
> — Writing code & completing functions → GitHub Copilot (stays in your editor)
> — "Explain this architecture" / "review my Bicep file" → Claude (best at long context + reasoning)
> — Quick one-liners / general Q&A → any

---

### Installing GitHub Copilot

**Option 1 — VS Code (recommended)**
1. Install the [GitHub Copilot extension](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot)
2. Sign in with your GitHub account
3. `Ctrl+I` / `Cmd+I` to open inline chat · `Ctrl+Shift+I` for the full chat panel

**Option 2 — GitHub Copilot CLI** *(ask your terminal questions)*
```bash
# Install
npm install -g @githubnext/github-copilot-cli   # legacy
# or via GitHub CLI extension (current)
gh extension install github/gh-copilot

# Use it
gh copilot suggest "az command to list all VMs across all resource groups"
gh copilot explain "az group deployment create --what-if"
```

**Option 3 — GitHub Copilot Desktop** *(standalone chat app)*

Download the desktop app — works outside your editor, useful for longer conversations and code reviews.

🔗 [desktop.github.com/copilot](https://desktop.github.com) → Sign in → Copilot tab

<img src="screenshots/github-copilot-vscode.png" alt="GitHub Copilot in VS Code" width="640">

---

### Installing Claude

**Option 1 — Web**
🔗 [claude.ai](https://claude.ai) — free tier available, Pro for Claude Sonnet/Opus

**Option 2 — Claude Desktop** *(best option — runs locally, can access local files)*
1. Download from [claude.ai/download](https://claude.ai/download)
2. Sign in with your Anthropic account
3. Enable **MCP (Model Context Protocol)** tools for local file/git access

```
Claude Desktop features:
✓ Drag-and-drop files and images
✓ Projects — persistent memory across conversations
✓ MCP integrations (read local files, run commands, browse the web)
✓ Extended context window (200k tokens — paste entire codebases)
```

**Option 3 — API**
```bash
pip install anthropic

python - <<'EOF'
import anthropic
client = anthropic.Anthropic()
msg = client.messages.create(
    model="claude-opus-4-5",
    max_tokens=1024,
    messages=[{"role": "user", "content": "Review this Bicep template: ..."}]
)
print(msg.content[0].text)
EOF
```

🔗 [docs.anthropic.com](https://docs.anthropic.com) · [API pricing](https://www.anthropic.com/pricing)

<img src="screenshots/claude-desktop.png" alt="Claude Desktop" width="640">

---

## 💻 CLI & Shell

### ⭐ Azure CLI
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free-green)
![badge](https://img.shields.io/badge/Open_Source-black?logo=github)

The single most useful tool for day-to-day Azure work. Cross-platform, fast, scriptable. Learns quickly.

```bash
# Login
az login

# List all your subscriptions
az account list --output table

# Deploy a resource group
az group create --name MyRG --location norwayeast
```

**Best for:** Scripting, CI/CD pipelines, anything you do more than once.
**Not ideal for:** One-off exploration → use the Portal for that.

📖 [Docs](https://learn.microsoft.com/cli/azure/) · [Command reference (A–Z)](https://learn.microsoft.com/cli/azure/reference-index)

<img src="screenshots/azure-cli.png" alt="Azure CLI in action" width="640">
<br><sub>💡 Add your own screenshot — see <a href="screenshots/README.md">screenshots/README.md</a></sub>

---

### Azure PowerShell
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free-green)

Same reach as Azure CLI but in PowerShell syntax. Prefer this if your team lives in PowerShell or you're writing Windows-native scripts.

```powershell
Connect-AzAccount
Get-AzResourceGroup | Select-Object ResourceGroupName, Location
```

📖 [Docs](https://learn.microsoft.com/powershell/azure/) · [Module reference](https://learn.microsoft.com/powershell/module/az.resources/)

---

### ⭐ Azure Cloud Shell
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free-green)

Browser-based shell built into the Azure Portal. Has Azure CLI, PowerShell, git, kubectl, Terraform, Bicep — all pre-installed. Fastest way to run a quick command on any machine.

**Open it:** Click the `>_` icon in the top bar of [portal.azure.com](https://portal.azure.com), or go to [shell.azure.com](https://shell.azure.com).

<img src="screenshots/cloud-shell.png" alt="Azure Cloud Shell" width="640">

---

### Azure Developer CLI (`azd`)
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Open_Source-black?logo=github)
![badge](https://img.shields.io/badge/Free-green)

Higher-level than Azure CLI — opinionated workflow for provisioning + deploying apps in one command. Pairs with Bicep templates.

```bash
azd up        # provision infra + deploy app in one shot
azd down      # tear everything down
azd monitor   # open Application Insights
```

📖 [Docs](https://learn.microsoft.com/azure/developer/azure-developer-cli/) · [Template gallery](https://azure.github.io/awesome-azd/)

---

## 🏗️ Infrastructure as Code

### ⭐ Bicep
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Open_Source-black?logo=github)
![badge](https://img.shields.io/badge/Free-green)

Azure's own IaC language. Cleaner than ARM JSON, first-class Azure support, no state file needed (unlike Terraform). If you're Azure-only, this is the right choice.

```bicep
resource storageAccount 'Microsoft.Storage/storageAccounts@2023-01-01' = {
  name: 'mystorageaccount'
  location: resourceGroup().location
  sku: { name: 'Standard_LRS' }
  kind: 'StorageV2'
}
```

**VS Code extension:** [Bicep extension](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-bicep) — IntelliSense, type checking, `bicep decompile` to convert existing ARM.

📖 [Docs](https://learn.microsoft.com/azure/azure-resource-manager/bicep/) · [Quickstart templates](https://github.com/Azure/azure-quickstart-templates)

<img src="screenshots/bicep-vscode.png" alt="Bicep in VS Code" width="640">

---

### Terraform (Azure Provider)
![badge](https://img.shields.io/badge/HashiCorp-7B42BC?logo=terraform&logoColor=white)
![badge](https://img.shields.io/badge/Open_Source-black?logo=github)
![badge](https://img.shields.io/badge/Free-green)

Best choice if you manage **multiple clouds** (Azure + AWS + GCP). Larger community than Bicep, mature ecosystem.

```hcl
provider "azurerm" {
  features {}
}

resource "azurerm_resource_group" "main" {
  name     = "my-rg"
  location = "norwayeast"
}
```

📖 [Azure Provider docs](https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs) · [AzureRM examples](https://github.com/hashicorp/terraform-provider-azurerm/tree/main/examples)

> **Bicep vs Terraform?** Azure-only shop → Bicep. Multi-cloud or large team → Terraform.

---

### ARM Templates
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)

The predecessor to Bicep. JSON-based, verbose, harder to read. Use Bicep instead for new work — ARM is still useful when you need to export an existing resource.

📖 [Quickstart templates (GitHub)](https://github.com/Azure/azure-quickstart-templates)

> **Tip:** Export any existing resource to ARM JSON from the portal (Resource → Export template), then use `bicep decompile` to convert it.

---

## 💰 Cost & Billing

### ⭐ Azure Cost Management + Billing
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free-green)

Built into the portal. Set budgets, alerts, and analyse spend by resource group, tag, or service. The Cost Analysis view is particularly good.

**Portal:** Cost Management + Billing → Cost Analysis

**Most useful features:**
- **Budgets + alerts** — get emailed when spend hits 80% of budget
- **Cost by tag** — tag your resources with `env:prod` / `team:backend` and split costs
- **Forecasting** — projects next 30 days based on current trend

<img src="screenshots/cost-management.png" alt="Azure Cost Management" width="640">

📖 [Docs](https://learn.microsoft.com/azure/cost-management-billing/)

---

### Azure Pricing Calculator
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free-green)

Build a "basket" of Azure services before you deploy them and get a monthly estimate. Share estimates with a URL.

🔗 [azure.microsoft.com/pricing/calculator](https://azure.microsoft.com/en-us/pricing/calculator/)

---

### AzurePrice.net
![badge](https://img.shields.io/badge/Community-orange)
![badge](https://img.shields.io/badge/Free-green)

Fastest way to compare VM sizes and prices across regions. Much quicker than navigating the official pricing pages.

🔗 [azureprice.net](https://azureprice.net)

<img src="screenshots/azureprice.png" alt="AzurePrice.net" width="640">

---

### Azure Advisor
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free-green)

Automated recommendations for cost, security, reliability, performance, and operational excellence. Check it monthly — it will usually find idle resources or overprovisioned VMs.

**Portal:** Search "Advisor" in the portal

---

## 📊 Monitoring & Observability

### ⭐ Application Insights
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free_tier-green)

The best Azure monitoring tool for developers. Add the SDK to your app and get: request traces, exceptions, dependency calls, performance, user flows — all in one place.

**Best features:**
- **Live Metrics** — real-time request/failure stream
- **Transaction search** — find a specific request end-to-end
- **Failures blade** — exceptions grouped and ranked by frequency
- **Smart Detection** — AI-powered anomaly alerts (no setup required)

<img src="screenshots/app-insights.png" alt="Application Insights" width="640">

📖 [Docs](https://learn.microsoft.com/azure/azure-monitor/app/app-insights-overview)

---

### Azure Monitor
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free_tier-green)

The platform under everything — metrics, logs, alerts, workbooks. Think of it as the umbrella; App Insights and Log Analytics are features inside it.

**Key sub-tools:**
- **Metrics Explorer** — time-series graphs for any Azure resource
- **Workbooks** — combine charts, queries, and text into shareable reports
- **Alerts** — fire on metric thresholds or KQL queries

📖 [Docs](https://learn.microsoft.com/azure/azure-monitor/)

---

### Log Analytics / KQL
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free_tier-green)

Query your logs using **KQL (Kusto Query Language)**. Steep-ish learning curve but incredibly powerful once you know it.

```kql
// Requests with > 1s duration, last hour
requests
| where timestamp > ago(1h)
| where duration > 1000
| summarize count() by name, bin(timestamp, 5m)
| render timechart
```

📖 [KQL quick reference](https://learn.microsoft.com/azure/data-explorer/kql-quick-reference) · [KQL playground](https://dataexplorer.azure.com/clusters/help/databases/Samples)

---

### Azure Managed Grafana
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Paid-red)

Fully managed Grafana with native Azure Monitor integration. Use when you want Grafana dashboards without managing the server yourself.

📖 [Docs](https://learn.microsoft.com/azure/managed-grafana/)

---

## 🔒 Security & Identity

### ⭐ Microsoft Defender for Cloud
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free_tier-green)

The security posture dashboard for your Azure environment. Gives you a **Secure Score** and a prioritised list of recommendations. The free tier alone is valuable — turn it on from day one.

**What to check weekly:**
- Secure Score trend
- Active recommendations (sort by severity)
- Active alerts

<img src="screenshots/defender-for-cloud.png" alt="Microsoft Defender for Cloud" width="640">

📖 [Docs](https://learn.microsoft.com/azure/defender-for-cloud/)

---

### Microsoft Entra ID (Azure AD)
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free_tier-green)

Identity platform — users, groups, app registrations, managed identities, conditional access. The backbone of Azure access control.

**Key concepts to know:**
- **Managed Identity** — give an Azure resource an identity so it can talk to other Azure services *without storing credentials anywhere*
- **App Registration** — register your own applications to use Microsoft identity
- **Conditional Access** — enforce MFA, block risky sign-ins

📖 [Docs](https://learn.microsoft.com/entra/identity/)

---

### Azure Key Vault
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Paid-red)

Store secrets, keys, and certificates. Never put connection strings in app config or code — put them in Key Vault and reference them with a URI. Works with Managed Identity so your app reads secrets without any stored credentials.

```bash
# Store a secret
az keyvault secret set --vault-name my-vault --name DbPassword --value "s3cr3t!"

# Read it in your app (using Managed Identity — no credentials needed)
```

📖 [Docs](https://learn.microsoft.com/azure/key-vault/)

---

### Microsoft Sentinel
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Paid-red)

Cloud-native SIEM/SOAR. For teams that need real security operations — threat hunting, incident management, automated response. Overkill for small setups; essential for enterprise.

📖 [Docs](https://learn.microsoft.com/azure/sentinel/)

---

## 🚢 DevOps & Deployment

### ⭐ GitHub Actions for Azure
![badge](https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white)
![badge](https://img.shields.io/badge/Free_tier-green)

If your code is on GitHub, this is the easiest path to deploy to Azure. Official Microsoft actions for everything: `azure/login`, `azure/cli`, `azure/webapps-deploy`, `azure/bicep-deploy`.

```yaml
- name: Login to Azure
  uses: azure/login@v2
  with:
    creds: ${{ secrets.AZURE_CREDENTIALS }}

- name: Deploy to App Service
  uses: azure/webapps-deploy@v3
  with:
    app-name: my-app
    package: ./dist
```

📖 [Action catalogue](https://github.com/Azure/actions) · [Workflow templates](https://learn.microsoft.com/azure/app-service/deploy-github-actions)

---

### Azure DevOps
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free_tier-green)

Microsoft's all-in-one DevOps platform: Boards (work items), Repos (git), Pipelines (CI/CD), Test Plans, Artifacts (package feeds). Best when your whole team is in the Microsoft ecosystem.

**Free for:** 5 users + unlimited public projects

🔗 [dev.azure.com](https://dev.azure.com) · 📖 [Docs](https://learn.microsoft.com/azure/devops/)

<img src="screenshots/azure-devops.png" alt="Azure DevOps Pipelines" width="640">

---

### Azure Container Registry (ACR)
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Paid-red)

Private Docker registry tightly integrated with AKS, Azure Container Apps, and App Service. Use ACR Tasks to build images in the cloud without a local Docker daemon.

📖 [Docs](https://learn.microsoft.com/azure/container-registry/)

---

## 🤖 AI & Copilot

### ⭐ GitHub Copilot
![badge](https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white)
![badge](https://img.shields.io/badge/Paid_(free_for_students)-green)

The best AI tool for writing code. Lives inside your editor — completions as you type, inline chat for refactoring, a full chat panel for bigger questions. Now covers the whole dev workflow: code, tests, PRs, CLI.

**Where it lives:**
| Surface | What you get |
|---------|-------------|
| VS Code / JetBrains / Neovim | Inline completions + chat |
| GitHub.com | PR summaries, code review, explain commit |
| Terminal (via `gh copilot`) | Suggest & explain shell commands |
| Desktop app | Standalone chat, outside your editor |

**Killer features for Azure devs:**
- Ask it to write Bicep/Terraform/YAML from a plain English description
- `gh copilot suggest` in the terminal — never forget an `az` command again
- Explain any error message by pasting it into chat

🔗 [github.com/features/copilot](https://github.com/features/copilot) · [Pricing](https://github.com/features/copilot#pricing)

<img src="screenshots/github-copilot-vscode.png" alt="GitHub Copilot in VS Code" width="640">

---

### ⭐ Claude (Anthropic)
![badge](https://img.shields.io/badge/Anthropic-orange)
![badge](https://img.shields.io/badge/Free_tier-green)

The best AI for long-context reasoning — architecture decisions, reviewing long Bicep/Terraform files, drafting runbooks, explaining complex concepts. 200k token context window means you can paste an entire codebase.

**Where it lives:**
| Surface | What you get |
|---------|-------------|
| [claude.ai](https://claude.ai) | Web app, free tier (Claude Sonnet) |
| Claude Desktop | Native app, file drag-and-drop, MCP tools |
| API | Integrate into your own apps |

**Most useful for Azure work:**
- Paste a full ARM/Bicep template → "What does this do? What are the security risks?"
- "Design the infrastructure for X workload on Azure, with cost in mind"
- Draft architecture decision records (ADRs) and runbooks
- Review IaC PRs — paste the diff and ask for a critique

**Claude Desktop tips:**
- Enable Projects for persistent memory per client/workload
- Use MCP file server to give Claude read access to your local repo — no more pasting

🔗 [claude.ai](https://claude.ai) · [Desktop download](https://claude.ai/download) · [API docs](https://docs.anthropic.com)

<img src="screenshots/claude-desktop.png" alt="Claude Desktop" width="640">

---

### Azure OpenAI Service
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Paid-red)

GPT-4o, o1, DALL·E, Whisper, and Embeddings — via an Azure endpoint inside your subscription. Data stays in your Azure region, subject to your compliance policies. The right choice over the openai.com API when data sovereignty matters.

**vs openai.com API:** Same models, same performance — but your data doesn't leave your Azure tenant, you get SLAs, and it integrates with Entra ID for auth.

📖 [Docs](https://learn.microsoft.com/azure/ai-services/openai/) · [Model comparison](https://learn.microsoft.com/azure/ai-services/openai/concepts/models)

---

### Azure AI Foundry (formerly AI Studio)
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free_tier-green)

The unified workspace for building AI apps on Azure: model catalogue (OpenAI + Meta + Mistral + others), prompt flow, evaluation, deployment. Good visual playground for testing models before committing code.

🔗 [ai.azure.com](https://ai.azure.com) · 📖 [Docs](https://learn.microsoft.com/azure/ai-foundry/)

<img src="screenshots/ai-foundry.png" alt="Azure AI Foundry" width="640">

---

### Copilot in Azure Portal
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Preview-orange)

AI assistant built directly into the Azure Portal. Ask it questions about your live resources — it can see your actual subscription context.

**Good prompts to try:**
- *"Why is my App Service CPU at 90%?"*
- *"Write a KQL query to find all failed requests in the last hour"*
- *"What's the cheapest VM SKU that supports Premium SSD in norwayeast?"*

**Activate:** Click the ✨ Copilot icon in the portal top bar.

---

## 🗄️ Data & Storage

### ⭐ Azure Storage Explorer
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free-green)
![badge](https://img.shields.io/badge/Open_Source-black?logo=github)

Desktop app (Windows/Mac/Linux) for browsing blobs, queues, tables, and file shares. Drag-and-drop upload, SAS token generation, and emulator support built in.

🔗 [Download](https://azure.microsoft.com/features/storage-explorer/) · 📖 [Docs](https://learn.microsoft.com/azure/vs-azure-tools-storage-manage-with-storage-explorer)

<img src="screenshots/storage-explorer.png" alt="Azure Storage Explorer" width="640">

---

### AzCopy
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free-green)
![badge](https://img.shields.io/badge/Open_Source-black?logo=github)

Command-line tool for high-speed bulk transfers to/from Azure Storage. Much faster than portal uploads for large files.

```bash
# Copy a local folder to a blob container
azcopy copy './data/*' 'https://mystorage.blob.core.windows.net/mycontainer/' --recursive

# Sync (like rsync)
azcopy sync './data' 'https://mystorage.blob.core.windows.net/mycontainer/'
```

🔗 [Download](https://learn.microsoft.com/azure/storage/common/storage-use-azcopy-v10)

---

### Azure Data Studio
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free-green)
![badge](https://img.shields.io/badge/Open_Source-black?logo=github)

VS Code-like editor for Azure SQL, SQL Server, and PostgreSQL. Notebooks, query history, and visualisation built in. Lighter than SSMS.

🔗 [Download](https://learn.microsoft.com/sql/azure-data-studio/download-azure-data-studio)

---

## 📐 Architecture & Design

### ⭐ Azure Architecture Center
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free-green)

Reference architectures, design patterns, best-practice guides, and decision trees for every Azure workload type. If you're designing something from scratch, start here.

🔗 [learn.microsoft.com/azure/architecture](https://learn.microsoft.com/azure/architecture/)

**Most useful sections:**
- [Well-Architected Framework](https://learn.microsoft.com/azure/well-architected/) — evaluate your design across 5 pillars (Reliability, Security, Cost, Performance, Operations)
- [Reference architectures](https://learn.microsoft.com/azure/architecture/browse/) — browse by workload type
- [Cloud design patterns](https://learn.microsoft.com/azure/architecture/patterns/) — Retry, Circuit Breaker, CQRS, Saga, etc.

---

### Azure Diagrams (draw.io / diagrams.net)
![badge](https://img.shields.io/badge/Open_Source-black?logo=github)
![badge](https://img.shields.io/badge/Free-green)

diagrams.net (draw.io) has a full Azure icon set built in. Best free tool for drawing Azure architecture diagrams.

**To enable:** In diagrams.net → Extras → Edit Diagram → or use the Azure shape library from the shapes panel.

🔗 [app.diagrams.net](https://app.diagrams.net)

---

### Azure Resource Visualizer
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free-green)

Visualise ARM/Bicep templates as a diagram before deploying. Built into the portal and VS Code Bicep extension.

**VS Code:** Open any `.bicep` file → right-click → Open Bicep Visualizer

---

## 🔌 VS Code Extensions

Install these if you're doing any Azure development in VS Code:

| Extension | What it does |
|-----------|-------------|
| ⭐ [Bicep](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-bicep) | IntelliSense, validation, visualiser for Bicep IaC |
| ⭐ [Azure Tools](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) | Pack of all Azure extensions in one install |
| [Azure Resources](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureresourcegroups) | Browse and manage Azure resources from the sidebar |
| [Azure Functions](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azurefunctions) | Create, debug, deploy Functions without leaving VS Code |
| [Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker) | Manage containers, push to ACR |
| [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) | Supercharged git — essential when managing IaC changes |
| [REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client) | Test Azure REST APIs directly in `.http` files |
| [HashiCorp Terraform](https://marketplace.visualstudio.com/items?itemName=hashicorp.terraform) | Terraform HCL IntelliSense and formatting |

<img src="screenshots/vscode-extensions.png" alt="VS Code Azure extensions" width="640">

---

## 📚 Learning & Certs

### ⭐ Microsoft Learn
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free-green)

Free, structured learning paths for every Azure service and certification. Includes sandbox environments — you practice in a real Azure subscription without needing your own.

🔗 [learn.microsoft.com/training](https://learn.microsoft.com/training/)

---

### Azure Certifications path

```
Beginner                    Associate                        Expert
────────────                ─────────────────────────────    ──────────────────────
AZ-900 Fundamentals   →     AZ-104 Administrator        →    AZ-305 Solutions Architect
                      →     AZ-204 Developer             →    AZ-400 DevOps Engineer
                      →     AZ-500 Security Engineer
                      →     AI-102 AI Engineer
```

🔗 [Certification overview](https://learn.microsoft.com/certifications/azure/) · [Practice assessments (free)](https://learn.microsoft.com/certifications/practice-assessments-for-microsoft-certifications)

---

### John Savill's Azure Masterclass
![badge](https://img.shields.io/badge/YouTube-FF0000?logo=youtube&logoColor=white)
![badge](https://img.shields.io/badge/Free-green)

The best free deep-dive Azure content on YouTube. Whiteboard-style, technically rigorous, covers everything from fundamentals to AZ-305 prep.

🔗 [YouTube channel](https://www.youtube.com/@NTFAQGuy) · [Azure Masterclass playlist](https://www.youtube.com/playlist?list=PLlVtbbG169nGccbp8VSpAozu3w9xSANRk)

---

### Azure Friday
![badge](https://img.shields.io/badge/Microsoft_Official-0078d4?logo=microsoft-azure&logoColor=white)
![badge](https://img.shields.io/badge/Free-green)

Short (15–20 min) demo videos by the Azure product teams. Good for staying current with new features.

🔗 [learn.microsoft.com/shows/azure-friday](https://learn.microsoft.com/shows/azure-friday/)

---

## 🔗 Quick Reference Links

| What | Link |
|------|------|
| Azure Portal | [portal.azure.com](https://portal.azure.com) |
| Azure Cloud Shell | [shell.azure.com](https://shell.azure.com) |
| Azure Status | [status.azure.com](https://status.azure.com) |
| Azure Docs | [learn.microsoft.com/azure](https://learn.microsoft.com/azure) |
| Azure Architecture Center | [learn.microsoft.com/azure/architecture](https://learn.microsoft.com/azure/architecture) |
| Pricing Calculator | [azure.microsoft.com/pricing/calculator](https://azure.microsoft.com/en-us/pricing/calculator/) |
| VM Price Comparison | [azureprice.net](https://azureprice.net) |
| Azure Updates (new features) | [azure.microsoft.com/updates](https://azure.microsoft.com/en-us/updates/) |
| Azure CLI Reference | [learn.microsoft.com/cli/azure/reference-index](https://learn.microsoft.com/cli/azure/reference-index) |
| KQL Reference | [learn.microsoft.com/azure/data-explorer/kql-quick-reference](https://learn.microsoft.com/azure/data-explorer/kql-quick-reference) |
| Bicep playground | [aka.ms/bicepdemo](https://aka.ms/bicepdemo) |
| Azure Quickstart Templates | [github.com/Azure/azure-quickstart-templates](https://github.com/Azure/azure-quickstart-templates) |
| Microsoft Learn | [learn.microsoft.com/training](https://learn.microsoft.com/training/) |
| Azure AI Foundry | [ai.azure.com](https://ai.azure.com) |
| Azure DevOps | [dev.azure.com](https://dev.azure.com) |

---

<div align="center">
<sub>Maintained by <a href="https://github.com/bjadda">bjadda</a> · Contributions welcome via PR</sub>
</div>