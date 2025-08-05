# Getting Started - Actions and Dynamic Actions

Sophrosyne uses two types of executable elements to counter Alerts: **Actions** and **Dynamic Actions**. Both can be triggered automatically (via REST) or manually (via WebUI). The main difference is whether runtime parameters are supported.

---

## Action

An **Action** is a predefined command that executes exactly as specified, without additional parameters at runtime.

```yaml
Action:
  type: object
  properties:
    id:
      type: string
      example: id_1
    name:
      type: string
      example: AnsibleDeployment
    description:
      type: string
      example: This starts the deployment of your data center with Ansible
    command:
      type: string
      example: ansible-playbook
    version:
      type: string
      example: v.1.2.3
    postExecutionLogFilePath:
      type: string
      example: /etc/ansible/ansible.log
    allowedApikeys:
      type: array
      items:
        type: string
    requiresConfirmation:
      type: int
      example: 1
    muted:
      type: int
      example: 1
```

### Key Fields

* **`command`**: Base command to execute.
  Examples:

  * `ansible-playbook`
  * `bash`
  * `/bin/my_executable`
  * `echo Hello World`

* **`postExecutionLogFilePath`**: Optional log file path to retrieve execution logs after the action completes.

* **`allowedApikeys`**: Defines which API keys can trigger this Action.

* **`requiresConfirmation`**: When set, the Action will only execute after explicit user approval.

* **`muted`**: If muted, the Action is automatically rejected when triggered.

---

## Dynamic Action

A **Dynamic Action** allows parameterized execution, where runtime values are injected into the command through placeholders.

```yaml
DynamicAction:
  type: object
  properties:
    id:
      type: string
      example: id_1
    name:
      type: string
      example: AnsibleDeployment
    description:
      type: string
      example: This starts the deployment of your data center with Ansible
    command:
      type: string
      example: ansible-playbook
    dynamicParameters:
      type: string
      example: -i {{inventory}} {{playbook}}
    version:
      type: string
      example: v.1.2.3
    postExecutionLogFilePath:
      type: string
      example: /etc/ansible/ansible.log
    allowedApikeys:
      type: array
      items:
        type: string
    requiresConfirmation:
      type: int
      example: 1
    keepLatestConfirmationRequest:
      type: int
      example: 1
    muted:
      type: int
      example: 1
```

### Key Fields

* **`command`**: The static part of the command to be executed.
  Example: `ansible-playbook`

* **`dynamicParameters`**: Defines parameters required at runtime.
  Placeholders must use **interpolation** syntax `{{ }}`.
  Example:

  ```
  -i {{inventory}} {{playbook}}.yml
  ```

  Here, the system will ask the user to provide values for `inventory` and `playbook` before execution.

* **`postExecutionLogFilePath`**: Optional path to retrieve logs after execution.

* **`allowedApikeys`**: Restricts which API keys can trigger this Dynamic Action.

* **`requiresConfirmation`**: Forces user confirmation before execution.

* **`keepLatestConfirmationRequest`**: If multiple confirmation requests for the same Action exist with different parameters, determines whether to override the latest request or add a new one.

* **`muted`**: Prevents execution when enabled.

---

## Complex Commands

* Use **double quotes (`""`)** to wrap commands with multiple arguments.
* If your command itself contains double quotes, wrap it in **single quotes (`''`)**.

---

## Confirmation Workflow

Both Actions and Dynamic Actions may require additional user confirmation before execution. When this setting is enabled, the Action will not run until explicitly approved in the confirmation queue.

---

### Summary

* Use **Actions** for fixed, predefined commands.
* Use **Dynamic Actions** for commands needing runtime parameters.
* Configure logging, confirmation behavior, and API key restrictions to suit your operational needs.
