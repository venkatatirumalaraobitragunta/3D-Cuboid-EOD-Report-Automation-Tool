Project Demo Link :https://script.google.com/macros/s/AKfycbyImb2Jq7ExqjwjirDfGS9eWvJ0fnuZAylNIJRyn7BtTJ316EBvdun5grgGatkPgA/exec
3D Cuboid EOD Report Automation Tool
A web-based tool built with Google Apps Script, HTML, CSS, and JavaScript to support production time allocation and End-of-Day (EOD) reporting for 3D cuboid annotation workflows.
Overview
The tool helps users organize task details, calculate estimated allocation timelines, review shift workload, and prepare EOD summaries. It includes a browser-based interface backed by Google Apps Script.
Features
- Shift configuration: Select a work date, location, and predefined shift, or enter a custom shift window.
- Downtime handling: Include downtime when calculating the effective shift duration.
- Task management: Add, remove, or bulk-paste task rows and enter batch/task identifiers, annotation counts, and task status.
- Input validation: Checks required Task IDs and prevents duplicate Task IDs within an allocation request.
- Allocation generation: Calculate a timeline using the configured ST and MT rates.
- Auto-fit allocation: Scale workload timing to fit the available shift duration.
- Workload and shift summaries: Review productive and non-productive time, counts, TPST, remaining time, and workload surplus/shift progress.
- Performance indicators: View status indicators and warnings based on allocation rates and workload.
- Google Form workflow: Open a prefilled form for a task and track the form workflow. With the current configuration, users manually confirm that the form was submitted.
- Export and copy tools: Export allocation results to CSV and copy an EOD summary or individual time values.
- Task search: Filter generated results by Task ID or Batch ID.
- User interface options: Dark mode, automatic local input saving, keyboard shortcuts, and a reference calculator.
- Feedback and activity tracking: Collect user feedback, track tool activity, and provide a developer-only live active-user view.
- Daily usage summary: An optional scheduled email summary of tool activity for the developer.
Technologies
- Google Apps Script
- JavaScript
- HTML5
- CSS3
- Google Sheets / Google Forms integration where configured
Project Structure
3D-Cuboid-EOD-Report-Automation/
├── Code.gs      # Apps Script backend, allocation logic, activity tracking, and feedback
├── Index.html   # Frontend interface, task inputs, results, and client-side interactions
└── README.md    # Project documentation
Allocation Defaults
The current source defines these default calculation values. Adjust them only when appropriate for your workflow:
Setting	Current value
Default ST rate	45 seconds per object
MT rate in Generate Allocation mode	360 seconds (6 minutes) per object
MT benchmark in Auto-Fit mode	450 seconds (7 minutes 30 seconds) per object
FP allocation	30 seconds per item
TC allocation	900 seconds (15 minutes) when present


Predefined shift windows are configured in Code.gs and mirrored in Index.html. Keep both configurations in sync if you change locations or shift timings.
Setup and Deployment
1. Create a new Google Apps Script project.
2. Add the backend code to Code.gs.
3. Create an HTML file named Index and add the frontend code from Index.html.
4. Review the configuration in Code.gs, including locations, shift windows, developer-only features, feedback email destination, and form-submission settings.
5. Review the corresponding location and shift configuration in Index.html and keep it synchronized with the backend.
6. Test the allocation calculations, CSV export, Google Form workflow, activity tracking, and feedback feature using non-production/sample data.
7. Deploy as a web app and choose access permissions appropriate to the intended users and your organization's policies.
8. If daily usage summaries are required, review and run setupDailyEodTrigger() once from the Apps Script editor. Confirm the trigger and email destination before enabling it.
Google Form Workflow
The tool opens a prefilled Google Form for task reporting. Google Form authentication and organization restrictions are controlled by Google Forms and the form owner's settings. Users may need to authenticate and submit the form manually. The current backend configuration leaves FORM_ID empty, so the interface uses manual confirmation instead of automatically verifying form responses.
Important Configuration and Security Notes
- Do not commit passwords, access tokens, private keys, real employee details, confidential task data, or internal-only links to a public repository.
- Review and sanitize organization-specific emails, Google Form URLs/IDs, spreadsheet IDs, and other identifiers before sharing the code.
- Use sample or synthetic data for screenshots and demonstrations.
- Keep the web app restricted to authorized users when required by company or client policy.
- The live active-user view is intended for the configured developer account. Review access checks before changing this behavior.
- Activity logging currently stores daily event logs in Apps Script Script Properties. Validate its behavior under expected concurrent usage before relying on it for high-volume production workloads.
- This project does not guarantee a specific concurrent-user capacity without load testing.
Limitations
- Automatic Google Form response verification is not enabled while FORM_ID is empty.
- Google Form authentication and final submission are handled by Google Forms; the web app does not bypass those requirements.
- The tool should be tested with representative sample data before production use or changes to calculation settings.
Disclaimer
This repository documents a workflow automation project. Share or publish the source only if you have permission to disclose the code and any organization-specific implementation details
