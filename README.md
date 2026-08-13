# TOH AI PMO Command Center — MVP Starter

This starter pack is used to build the first n8n workflow:

GitHub project data -> n8n -> Gemini -> Structured PMO analysis

## Files

- data/projects.json
  Demo IT project portfolio.
- prompts/project_health_system.txt
  System instructions for Gemini.
- schemas/project_health_output_schema.json
  JSON Schema for the n8n Structured Output Parser.

## Suggested GitHub repository

Create a repository named:

    toh-ai-pmo-command-center

Then copy these folders into the repository root.

## First workflow

Name the n8n workflow:

    PMO-01 Project Health Analyzer

Initial nodes:

1. Manual Trigger
2. HTTP Request - Load GitHub Portfolio
3. Code - Split Projects
4. Basic LLM Chain - Analyze Project
   - Google Gemini Chat Model
   - Structured Output Parser
5. Edit Fields - Add Run Metadata
6. Switch - Route by Health

Do not add Jira/Teams/email actions until the analysis output is stable.
