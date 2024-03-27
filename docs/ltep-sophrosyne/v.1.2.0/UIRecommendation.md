# Getting Started - WebUI

Get started with Sophrosyne's WebUI and explore the main functionalities of Sophrosyne.

## Action Recommendations

Sometimes, problems and alerts cannot be treated by executing Scripts and Code via Actions but require manual work from maintenance and expert teams. To support them and provide targeted guidance, Sophrosyne offers Action Recommendations. Action Recommendations are triggered the same way as Actions by Alerts. The difference is though that they do not execute an Action but show helpful information to counter the problem. Particularly, you can define who is responsible and how to contact them, provide an individual & html-rendering text with instructions or any kind of information and even attach a document with the same purpose.

### Create an Action Recommendation

Action Recommendations are designed to support maintenance and expert teams where Actions can not solve a problem or no Actions are available. Their prime objective is to ideally offer the exact information and instructions required to solve the source of an Alert. They are automatically triggered by a REST-Call originating from an Alert.

<h3>1. Navigate to Action Recommendation Menu</h3>

First navigate to the Action Recommendation Menu (1) and use the toolbar (2) to initiate the creation of a new Action Recommendation

<div style="text-align: center">
<img src="/ltep-sophrosyne/v.1.2.0/_media/ACTION_RECOMMENDATIONS_OVERVIEW.png" alt="ACTION_RECOMMENDATIONS_OVERVIEW" style="max-height:50vh">
</div>

<h3>2. Fill Action Recommendation Creation Form</h3>
After initiating the Action Recommendation creation, a form will pop up asking you to fill out the metadata for your Action Recommendation.<br/>

<div style="text-align: center">
<img src="/ltep-sophrosyne/v.1.2.0/_media/ACTION_RECOMMENDATIONS_CREATION_FORM.png" alt="ACTION_RECOMMENDATIONS_CREATION_FORM" style="max-height:50vh">
</div>

Fill the form out as described in the below manner:

<table style="width: 100%; border-collapse: collapse; margin-top: 20px;">
  <tr>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Field</th>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Description</th>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Properties</th>
    <th style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Example</th>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Recommendation Name</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">It is the human-readable identifier for your Action Recommendation</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Unique & Mandatory</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Cool Action Recommendation</td>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Action Description</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Typically, instructions, manuals or any kind of information to help counter the source of an Alert. Can be HTML-rendered</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Optional</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">&lt;strong&gt;DO THIS&lt;/strong&gt;&lt;br/&gt;&lt;p&gt;&lt;Thank you&lt;/p&gt;
</td>
  </tr>
    <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Responsible Entity</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Provide information about who to contact in case the respective Alert occurs</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Optional</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Team Webservices Development</td>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Contact</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Information about how to contact the responsible Entity</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Optional</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">webservice-development@mycompany.com</td>
  </tr>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Additional Documentation</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Attach any kind of PDF that might help to solve the source of an alert</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Optional</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Use the Mask</td>
  <tr>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Allowed Apikeys</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Choose the Apikey(s) that are accepted if an Action Recommendation shall be triggered automatically </td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">Optional/Inherently Mandatory</td>
    <td style="padding: 10px; text-align: left; border-bottom: 1px solid #ddd;">3V8CwBpNWcLakra3KlPKW8CjxDWfwTpKMuZgd2Om71u6EVBsADDyUd-4Hvmrsxug3rlrSGWNXLQXYUwz5bfftQ</td>
  </tr>
</table>

### Action Recommendation Prompts

When Alerts trigger an Action Recommendation, you can see them in the Action Confirmation and & Recommendation menu under the tab Active Recommendations. there you will find all triggered (active) Action Recommendations.

<div style="text-align: center">
<img src="/ltep-sophrosyne/v.1.2.0/_media/ACTION_RECOMMENDATION_OVERVIEW.png" alt="ACTION_RECOMMENDATION_OVERVIEW" style="max-height:50vh">
</div>