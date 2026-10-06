# EventWise — AI-Powered Event Planning Assistant

EventWise is a lightweight web application that turns event details into a practical, personalised event plan. It collects the event type, guest count, location, date, budget, and preferences, then uses an n8n workflow to create and store a plan.

## Features

- Account sign-up and sign-in
- AI-generated event plans tailored to the event details
- Budget, schedule, checklist, recommendations, weather, risks, and backup-plan sections
- Saved-plan retrieval, refresh, and checklist progress updates
- Responsive static frontend with no build step

## Project structure

- `index.html` — landing page
- `plan.html` — event-planning form
- `my-plan.html` — saved-plan view
- `script.js` — browser-side application logic
- `style.css` — styles
- `n8n json.json` — importable n8n workflow for the backend automation

## Run locally

This is a static site. Serve the folder through any local web server, then open it in a browser. For example, with VS Code's Live Server extension, open `index.html` using **Open with Live Server**.

## Configure n8n

1. Import `n8n json.json` into your n8n instance.
2. Activate and configure the workflow's credentials, database, AI, and any external services it uses.
3. Copy `config.js.example` to `config.js`.
4. Set `N8N_WEBHOOK_URL` in `config.js` to the production webhook URL from your n8n workflow.

`config.js` is ignored by Git so a private deployment URL can stay local. Do not commit credentials, API keys, tokens, or production secrets.

## Is the n8n JSON okay to include?

Yes. The workflow JSON is included deliberately so the automation can be imported and reproduced. Before sharing the repository publicly, review it for embedded credentials, webhook URLs, database details, or personally identifiable data. Exported credentials are normally not included by n8n, but connection names and configuration values may still reveal deployment information.

## Workflow contract

The frontend sends JSON `POST` requests to the configured webhook. It uses actions such as `signup`, `login`, `create_plan`, `get_plan`, and `update_plan`; workflow responses should be JSON and include `success`, plus the appropriate user, token, plan, version, and message fields.

## License

No license has been selected yet. Add a license file before reusing or distributing this project under defined terms.
