Welcome to Survey API documentation!
===================================

Here is an introduction on how to create a survey. We walk the user step-by-step through how to create the simplest possible example.

The topics covered include:

* Background material on JSON-RPC, security, etc.
* How to use the optional API Test tool (which you can use as a first step before you write your own JSON-RPC program) to test the JSON-RPC code needed to create a survey
* Survey Structure
* How to upload text or binary objects (i.e., audio, video, css, image) to use in a survey
* The APIs needed to create a survey
* How to export the survey responses

If would be good to first look at this page to understand the survey structure and object hierarchy. Then come back here.


Background Material on JSON-RPC, Security, etc.
------------------------------------------------

Next review this material on JSON-RPC.

* JSON RPC
* Required security http headers


DemoAllQuestions
-----------------

Ask support to send you a copy of **DemoAllQuestionTypes.json-rpc** as this demonstrates all question types in one very large survey.

Logic Flow
-----------

In order to have a complete survey we call each of these APIs:

* libraries_create—a library is a collection of surveys and survey objects. You can have different libraries as a way of grouping together surveys by some logical grouping.
* questions_create—questions exist independent of surveys. Thus you can use questions you define in different surveys.
* surveys_create—A survey is where you create pages and blocks and assign questions to the pages which are then assigned to the survey. This is also where you put targeting and quota logic. And you can add Javascript.
* surveyLinks_create—generates links for the survey. You can have different links for different audiences. And you can put quotas there, to have different quotas for different distributions (targets).
* surveys_set_status—this makes the survey available for use. The links you created above are displayed to the user at this point so that you can give them to respondents.

.. note::
   
      Note that as you create objects you assign names that you pass to the next logical section. For example, when you create a survey you give the survey a name say, XXX. So when you set the survey status you would use the name XXX in the survey attribute. But remember that each operation requires a name. So you need a name there as well. To keep things simple just use the survey name in the name attribute of the newly-created object or operation.

      The name is different than the id. An id is needed for each JSON-RPC call. It should be descriptive but you won't need it anywhere. To clarify. The id might be createSurvey. And the question type is gender. In the Page you use the name gender. But even that reference requires a name again. So you might put gender again just to not have too many names. But you could have called that usage of the question gender a1 or anything. Every object needs a name.

