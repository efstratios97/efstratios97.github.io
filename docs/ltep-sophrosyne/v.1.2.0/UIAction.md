# Getting Started - Actions UI

Get started with Sophrosyne's WebUI and explore the main functionalities of Sophrosyne.

## Action & Dynamic Action

An Action can be any piece of software or command that is designed to automatically counter the source of an Alert. It can be automatically triggered by a REST-Call originating from an Alert or manually via the Sophrosyne's Web-Interface. 

However, there are two main subtypes of Action: A (simple) Action and a Dynamic Action:

<div style="text-align: center">
<img src="/ltep-sophrosyne/v.1.2.0/_media/ACTIONS_TYPES.png" alt="ACTIONS_TYPES" style="max-height:15vh">
</div>

### Create a (simple) Action

An Action can be any piece of software or command that is designed to automatically counter the source of an Alert. It can be automatically triggered by a REST-Call originating from an Alert or manually via the Sophrosyne's Web-Interface. However, it does not offer the possibility to pass any parameters at execution time.

<h3>1. Navigate to Action Menu</h3>

First navigate to the Actions Menu (1) and use the toolbar (2) to initiate the creation of a new Action

<div style="text-align: center">
<img src="/ltep-sophrosyne/v.1.2.0/_media/ACTIONS_OVERVIEW.png" alt="Action Overview" style="max-height:50vh">
</div>
<h3>2. Fill Action Creation Form</h3>
After initiating the Action creation a form will pop up asking you to fill out the metadata for your Action.
<div style="text-align: center">
<img src="/ltep-sophrosyne/v.1.2.0/_media/ACTIONS_CREATION_FORM.png" alt="ACTIONS_CREATION_FORM" style="max-height:50vh">
</div>

Fill the form out as described in the below manner.

<table style="width: 100%; border-collapse: collapse; margin-top: 20px;">
  <tr>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Field</th>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Description</th>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Properties</th>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Example</th>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Action Name</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">It is the human-readable identifier for your Action</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Unique & Mandatory</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Cool Action</td>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Action Description</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Typically, a description of what your Action does</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Optional</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">This Action does cool stuff</td>
  </tr>
    <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Action Version</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">A version for your Action to track development and execution</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Optional</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">v.1.0.0</td>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Action Command</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">The command that the action shall execute</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Mandatory</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">ping -n 5 127.0.0.1</td>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Action's post execution Logs (optional)</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">If you have a custom Logfile.</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Optional</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">/path/to/your/application/logs</td>
  </tr>
    <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Requires Confirmation</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">When the respective action gets triggered an additionally confirmation by an user is necessary. Further info <a href="#/ltep-sophrosyne/v.1.2.0/WebUI?id=action-confirmation-requests">here</a></td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Mandatory / Default FALSE</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">toggle button</td>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Allowed Apikeys</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Choose the Apikey(s) that are accepted if an Action shall be triggered automatically </td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Optional</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">3V8CwBpNWcLakra3KlPKW8CjxDWfwTpKMuZgd2Om71u6EVBsADDyUd-4Hvmrsxug3rlrSGWNXLQXYUwz5bfftQ</td>
  </tr>
</table>


<div style="background-color: #fff3cd; border: 1px solid #ffeeba; color: #856404; padding: 10px; margin-bottom: 15px; border-radius: 5px;">
  <b>For Windows Users</b><br/>
  <p>If your command is not in the path but callable via Window's cmd-prompt, you have to prepend (Respectively, for powershell or other services) <p style="font-family: monospace; background-color: #f0f0f0; padding: 5px; border-radius: 3px; border: 1px solid #ccc; overflow-x: auto;">cmd.exe /c</p></p>
  <p>Example using Windows Subsystem for Linux (WSL)</p>
  <p style="font-family: monospace; background-color: #f0f0f0; padding: 5px; border-radius: 3px; border: 1px solid #ccc; overflow-x: auto;">cmd.exe /c wsl ansible-playbook -i inventory.ini myAwesomePlaybook.yml</p>
</div>


### Execute a (simple) Action via WebUI

To execute your Action manually via Sophrosyne's WebUI navigate to the Actions menu (1) and open the Action's submenu. Press execute Action (2). You will be able to see the command logs and its execution status.

<div style="text-align: center">
<img src="/ltep-sophrosyne/v.1.2.0/_media/ACTIONS_EXECUTION.png" alt="ACTIONS_CREATION_FORM" style="max-height:50vh">
</div>

### Create a Dynamic Action

A Dynamic Action is similar to a (simple) Action. However, the key difference is its flexibility as parameters can be passed at execution time and are not static like in a (simple) Action. Hence, there are small differences in the Dynamic Action creation and execution compared to (simple) Actions.  

<h3>1. Navigate to Dynamic Action Menu</h3>

First navigate to the Actions Menu and use the toolbar to initiate the creation of a new Action


<h3>2. Fill Action Creation Form</h3>

After initiating the Dynamic Action creation a form will pop up asking you to fill out the metadata for your Action. Here , you can directly notice that there is an extra field asking you to pass Dynamic Action Parameters. This is also the key difference to (simple) Actions as described above. While a simple Action has the complete execution command completely pre-defined, a Dynamic Action gives you the opportunity to flexibly pass parameters at execution time. The placeholders for the parameters are defined using interpolation. E.g: ping -n {{execution_times}} {{address}}

<div style="text-align: center">
<img src="/ltep-sophrosyne/v.1.2.0/_media/DYNAMIC_ACTIONS_CREATION_FORM.png" alt="DYNAMIC_ACTIONS_CREATION_FORM" style="max-height:50vh">
</div>

Fill the form out as described in the below manner. The main differences to (simple) Actions are highlighted.

<table style="width: 100%; border-collapse: collapse; margin-top: 20px;">
  <tr>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Field</th>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Description</th>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Properties</th>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Example</th>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Dynamic Action Name</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">It is the human-readable identifier for your Dynamic Action</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Unique & Mandatory</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Cool Dynamic Action</td>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Dynamic Action Description</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Typically, a description of what your Dynamic Action does</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Optional</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">This Dynamic Action does cool stuff</td>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Dynamic Action Version</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">A version for your Action to track development and execution</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Optional</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">v.1.0.0</td>
  </tr>
  <tr style="background-color: #3498db; color: white;">
    <td style="padding: 30px; text-align: left; border-bottom: 1px solid #ddd; font-weight: bold; font-size: 21px;">Dynamic Action Command</td>
    <td style="padding: 30px; text-align: left; border-bottom: 1px solid #ddd; font-weight: bold; font-size: 21px;">The command that the action shall execute. With Dynamic Actions you typically just define the static components of your command</td>
    <td style="padding: 30px; text-align: left; border-bottom: 1px solid #ddd; font-weight: bold; font-size: 21px;">Mandatory</td>
    <td style="padding: 30px; text-align: left; border-bottom: 1px solid #ddd; font-weight: bold; font-size: 21px;">ping</td>
  </tr>
  <tr style="background-color: #3498db; color: white;">
    <td style="padding: 30px; text-align: left; border-bottom: 1px solid #ddd; font-weight: bold; font-size: 21px;">Dynamic Action Parameters</td>
    <td style="padding: 30px; text-align: left; border-bottom: 1px solid #ddd; font-weight: bold; font-size: 21px;">The parameters with placeholders that shall be replaced at execution time. With Dynamic Actions you typically define the placeholders using interpolation {{}}</td>
    <td style="padding: 30px; text-align: left; border-bottom: 1px solid #ddd; font-weight: bold; font-size: 21px;">Mandatory</td>
    <td style="padding: 30px; text-align: left; border-bottom: 1px solid #ddd; font-weight: bold; font-size: 21px;">-n {{execution_times}} {{address}}</td>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Dynamic Action's post execution Logs (optional)</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">If you have a custom Logfile.</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Optional</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">/path/to/your/application/logs</td>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Requires Confirmation</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">When the respective action gets triggered an additionally confirmation by an user is necessary. Further info <a href="#/ltep-sophrosyne/v.1.2.0/WebUI?id=action-confirmation-requests">here</a></td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Mandatory / Default FALSE</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">toggle button</td>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Allowed Apikeys</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Choose the Apikey(s) that are accepted if an Action shall be triggered automatically </td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Optional</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">3V8CwBpNWcLakra3KlPKW8CjxDWfwTpKMuZgd2Om71u6EVBsADDyUd-4Hvmrsxug3rlrSGWNXLQXYUwz5bfftQ</td>
  </tr>
</table>

<div style="background-color: #fff3cd; border: 1px solid #ffeeba; color: #856404; padding: 10px; margin-bottom: 15px; border-radius: 5px;">
  <b>Dynamic Action Command & Dynamic Action Parameters</b><br/>
  <p>Purposely, the boundaries between Dynamic Action Command & Dynamic Action Parameters is not strictly defined and enforced.</p>
  <p>For example in the above example you could have also have done:</p>
  <table style="width: 100%; border-collapse: collapse; margin-top: 20px;">
  <tr>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Field</th>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Description</th>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Properties</th>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Example</th>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Dynamic Action Command</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">The command that the action shall execute. With Dynamic Actions you typically just define the static components of your command</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Mandatory</td>
    <td style="padding: 30px; text-align: left; border-bottom: 1px solid #ddd; font-weight: bold; font-size: 21px; background-color: #3498db; color: white;">ping -n</td>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Dynamic Action Parameters</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">The parameters with placeholders that shall be replaced at execution time. With Dynamic Actions you typically define the placeholders using interpolation {{}}</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Mandatory</td>
    <td style="padding: 30px; text-align: left; border-bottom: 1px solid #ddd; font-weight: bold; font-size: 21px; background-color: #3498db; color: white;">{{execution_times}} {{address}}</td>
  </tr>
 
  </tr>
</table>
</div>

### Execute a Dynamic Action via WebUI

To execute your Dynamic Action manually via Sophrosyne's WebUI navigate to the Actions menu and open the Dynamic Action's submenu. Press execute Action. Then a modal will appear asking you to pass your parameters according to your interpolated placeholders. Fill it with your parameters like in the screenshot below.

<div style="text-align: center">
<img src="/ltep-sophrosyne/v.1.2.0/_media/DYNAMIC_ACTIONS_EXECUTION.png" alt="DYNAMIC_ACTIONS_EXECUTION" style="max-height:50vh">
</div>

### Action confirmation Requests

As you could see above in the Action creation section, you can set Actions requiring an additional confirmation. By doing so, these Actions will require an extra confirmation by the user before they get executed. You can find all Actions requesting confirmation in the Action Confirmation Menu element.

<div style="text-align: center">
<img src="/ltep-sophrosyne/v.1.2.0/_media/ACTION_CONFIRMATION_OVERVIEW.png" alt="ACTION_CONFIRMATION_OVERVIEW" style="max-height:50vh">
</div>

<div style="background-color: #fff3cd; border: 1px solid #ffeeba; color: #856404; padding: 10px; margin-bottom: 15px; border-radius: 5px;">
  <b>Executing manually Actions requiring Confirmation</b><br/>
  <p>If you execute Actions requiring confirmation manually, you will still have to confirm them in the Action Confirmation section</p>
  
</div>