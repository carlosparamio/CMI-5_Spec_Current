CMI-5 Runtime Environment 
---

**AICC DOCUMENT NUMBER:** CMI5-001  &nbsp;&nbsp; **Revision:** CURRENT WORKING DRAFT   
**THIS DOCUMENT IS CONTROLLED BY:** AICC CMI Subcommittee


#***WORKING DRAFT - NOT FOR IMPLEMENTATION***


---

>Caveats...
>
>Copyright &copy; 2012-2015 AICC, All rights reserved
>
>The information contained in this document has been assembled by the AICC as an
informational resource. Neither the AICC nor any of its members assumes nor shall any of
them have any responsibility for any use by anyone for any purpose of this document or of
the data which it contains. All use of this document is subject to the terms of the
license agreement contained within it.

----


## Table of Contents

[__Revision History__](#revhistory)

[__Contributors__](#contributors)

* [__1.0 Overview__](#overview)
  * [1.1 Scope](#scope)
* [__2.0 References__](#references)
* [__3.0 Definitions__](#definitions)
  * [3.1 Abbreviations and acronyms](#acronyms)
* [__4.0 Conformance__](#conformance)
  * [4.1 Assignable Unit (AU)](#au_conformance)
  * [4.2 Learning Management Systems (LMS)](#lms_conformance)
* [__5.0 Conceptual Model: Informative__](#concept)
* [__6.0 LMS Requirements__](#lms_requirements)
  * [6.1 Course structures](#course_structures)
  * [6.3 LMS Statement API Requirements](#lms_statement_api_requirements)
* [__7.0 AU Requirements__](#au_requirements)
  * [7.1 AU State API Requirements](#au_state_api_requirements)
  * [7.2 AU Statement API Requirements](#au_statement_api_requirements)
      * [7.2.1 Placement of sessionId in Statements](#placement)
      * [7.2.2 First Statement API Call](#first_statement_au)
      * [7.1.2 Last Statement Call](#last_statement_au)
* [__8.0 Content Launch Mechanisms__](#content_launch)
  * [8.1 Web (Browser) Environment](#browser_environment)
  * [8.2 Authorization Token Fetch URL](#fetch_url)
  * [8.3 Other Launch Environments](#other_environment)
* [__9.0 XAPI Statement Data Model__](#xapi_data_model)
  * [9.1 Statement ID](#ID)
  * [9.2 Actor](#Actor)
  * [9.3 Verbs](#verbs)
  * [9.4 Object](#Object)
      * [9.4.1 objectType](#objectType)
      * [9.4.2 Object ID](#Object_ID)
      * [9.4.3 Definition](#Definition)
  * [9.5 Result](#Result)
      * [9.5.1 Score](#Score)
      * [9.5.2 Success](#Success)
      * [9.5.3 Completion](#Completion)
      * [9.5.4 Duration](#Duration)
  * [9.6 Context](#Context)
      * [9.6.1 Registration](#Registration)
      * [9.6.2 ContextActivities] (#ContextActivities)
      * [9.6.3 Extensions](#extensions)
* [__10.0 XAPI State Data Model__](#xapi_state)
* [__11.0 XAPI Agent Profile Data Model__](#xapi_agent_profile)
* [__12.0 XAPI Activity Profile Data Model__](#xapi_activity_profile)

[__Bibliography__](#bibliography)

[__License Agreement__](#license_agreement)

------


<a name="revhistory"></a>	
## Revision History

__0.1 Convert Working Draft to Markdown in GitHub (Feb 20, 2013):__  

Converted existing working draft to markdown format from Microsoft Word.

All previous work from 2012 discarded.


<a name="contributors"></a> 
##Contributors

<table>
	<tr><th>Name:</th><th>Organization:</th></tr>
	<tr><td>Ed Cohen</td><td>AICC Infrastructure Subcommittee Chair</td></tr>
	<tr><td>Aaron Silvers</td><td>ADL</td></tr>
	<tr><td>Jonathan Poltrack</td><td>ADL</td></tr>
	<tr><td>Andy Johnson</td><td>ADL</td></tr>
	<tr><td>Tom Creighton</td><td>ADL</td></tr>
	<tr><td>Nik Hruska</td><td>ADL</td></tr>
	<tr><td>Avron Barr</td><td>The LETSI Foundation</td></tr>
	<tr><td>Mike Rustici</td><td>Rustici Software</td></tr>
	<tr><td>Ben Clark</td><td>Rustici Software</td></tr>
	<tr><td>Megan Bowe</td><td>Rustici Software</td></tr>
	<tr><td>Jacques Talvard</td><td>Airbus</td></tr>
	<tr><td>William A. McDonald</td><td>Boeing</td></tr>
	<tr><td>Ray Lowery</td><td>Pratt &amp; Whitney</td></tr>
	<tr><td>John Kleeman</td><td>Questionmark</td></tr>
	<tr><td>Kris Rockwell</td><td>Hybrid Learning Systems</td></tr>
	<tr><td>Paul Roberts</td><td>Questionmark</td></tr>
	<tr><td>Christopher Reynolds</td><td>Pelesys</td></tr>
	<tr><td>Mingrui Zheng</td><td>Pelesys</td></tr>
	<tr><td>Chris Sawwa</td><td>Meridian Knowledge Systems</td></tr>
	<tr><td>Michael Roberts</td><td>VTraining Room</td></tr>
	<tr><td>Thomas Person</td><td>(Formerly of Adobe)</td></tr>
	<tr><td>Andrew Down es</td><td>Epic Learning</td></tr>
	<tr><td>Henry Ryng</td><td>inXsol</td></tr>
	<tr><td>Art Werkenthin</td><td>RISC, Inc.</td></tr>
	<tr><td>Chris Handorf</td><td>Pearson</td></tr>
</table> 

-------

<a name="overview"></a>  
#1.0 Overview


This specification describes interoperable runtime communication between Learning
Management Systems (LMS) and Learning Activities.

<a name="scope"></a>  
##1.1 Scope

The scope of this specification is limited to following:

* Launch by a Learning Management Systems (LMS) of Learning Activities.
* Launch and Runtime environment used for LMS and Learning Activities.
* Runtime communication data and data transport between LMS systems and Learning Activities 
* LMS course definition as it pertains to runtime data used by Learning Activities.  
* Reporting Requirements for LMS systems

This specification references how to use the XAPI specification within this scope.

Other uses of the XAPI specification are outside the scope.

Uses of activities not explicitly defined above are outside of the scope of this specification.


<a name="references"></a> 
#2.0  References

The following referenced documents are indispensable for the application of this
specification. 

RFC 2396, “Uniform Resource Identifiers (URI): Generic Syntax,” August 1998.

“Experience API”, curent working draft, ADL, 2012-2013  
<https://github.com/adlnet/xAPI-Spec/blob/master/xAPI.md>

CMI5-002  – LMS Course Structure, curent working draft, AICC, 2013  
<https://github.com/AICC/CMI-5_Spec_Current/blob/master/cmi5_coursestructure.md>



<a name="definitions"></a>   
#3.0 Definitions  


For purposes of this specification, the following terms and definitions apply: 

* __Administrator__: The administrative user that manages the LMS and related systems.
Such a user performs tasks such as learner enrollment, course structure definition, and
report management. 

* __Assignable Unit (AU)__:  A learning presentation launched from an
LMS. The AU is the unit of tracking and management. The AU collects data on the learner
and sends it to the LMS system. An Learning Activity Provider maps to a single AU.  

* __Course__: A collection of assignable units, in a logical grouping. A course is typically 
an internal data structure. Courses are often assigned to learners and tracked by the LMS.

* __Course Structure__: A list of assignable units and launch parameters, with an implied
sequence, representing a course. Experience API (XAPI): XAPI is a runtime data
communication specification for learning content (AU) to send and receive data to an LRS.
The XAPI specification is referenced by this document is used to define the data transport
and the data model. 

* __Learner__: The end user viewing/using the learning content (Learning Activity).

* __Learning Activity Provider (AP)__:  Learning Activity Provider (AP) as defined in the
XAPI specification.

* __Learning Management System (LMS)__: A computer system that may include the
capabilities to register learners, launch learning presentations, analyze and report
learner performance, and track learners progress. LMS launching, reporting, and tracking
roles are the focus of the CMI5 specification.  The LMS must have an LRS as part of its
implementation.  The use of the term "LMS" in this document must refer to the combination of an LMS and an LRS.

* __Learning Records Store (LRS)__: As defined in the XAPI specification. In this 
specification, the LMS must implement an LRS with additional requirements as specified in
this document.


<a name="acronyms"></a> 
##3.1 Abbreviations and Acronyms
<BR>
__ADL__: Advanced Distributed Learning  
__AICC__: Aviation Industry Computer-Based Training Committee  
__API__: Application Programming Interface  
__CMI__: Computer Managed Instruction  
__LMS__: Learning Management System  
__LRS__: Learning Record Store  
__PII__: Personally Identifiable Information  
__URI__: Uniform Resource Identifier  
__URL__: Uniform Resource Locator  
__URN__: Uniform Resource Name  
__XAPI__: Experience API  
<BR>


<a name="conformance"></a>  
#4.0  Conformance

Conformance to this specification is defined in section. 

In this specification, “must” is to be interpreted as a requirement on an implementation;
“must not” is to be interpreted as a prohibition.

“Should” is to be interpreted as a recommendation for implementation; “should not” is to
be interpreted as the converse of “should”.

“May” is to be interpreted as a course of action that is permissible within the limits of
the specification; “need not” indicates a course of action that is not required.

Uses of XAPI specification outside the scope this specification do not affect conformance
with this specification.

<a name="au_conformance"></a> 
##4.1 Assignable Unit (AU)

An Assignable Unit must conform to all requirements listed in Section 7 – AU Requirements

An Assignable Unit must conform to all requirements as specified in the XAPI
specification (see References)

An Assignable Unit must not implement any features or functionality (optional or
mandatory) described in this specification in a non-conforming manner.

<a name="lms_conformance"></a> 
##4.2 Learning Management Systems (LMS)

LMS systems must conform to all requirements listed in Section 6 – LMS Requirements.

A LMS must conform to all LRS requirements as specified in the XAPI specification
(see References)

The LMS must not implement any features or functionality (optional or mandatory)
described in this specification in a non-conforming manner.


<a name="concept"></a> 
#5.0 Conceptual Model: Informative  

Synopsis of the CMI-5 model:

* An LMS imports a course structure which may contain one or more Assignable Units.
* An LMS administrative user assigns a course to a learner.
* A learner authenticates with an LMS or related system.
* A learner launches an Assignable Unit (learning content) from the LMS or associated
launching system.
* The LMS writes lauch data to the integrated LRS. 
* The Assignable Unit (AU) sends a message to the LMS requesting launch parameters and recovers
previous state information from the LMS.
* Learner views the AU content and performs the learning. During this time
the AU may request from and store data to the LMS.
* The learner exits the AU.
* The AU reports final tracking data to the LMS and issues a "terminated" message.
* The LMS makes the next AU(s) available to the learner based on results from the closed AU session and course structure parameters.
* Administrative users create and view reports of tracking data recorded by AU(s) for individual learners.

Responsibilities of the Assignable Unit:

* Parse the parameters from the launching environment to determine where the LMS location
is and initiate communication with the LMS.
* Acting as “client”, send and receive messages using the defined transport mechanism(s)
and associate commands as prescribed in this specification.
* Format all data per defined data types and vocabularies defined in this specification.
* Send an “terminated” message prior to terminating the learning activity’s execution.

Responsibilities of the LMS:

* Create and maintain course structures.
* Acting as a “server”, receive and reply to messages using the defined transport.
mechanism(s) and associate commands as prescribed in this specification.
* Format all data per defined data types and vocabularies defined in this specification.
* Launch AUs contained in courses, in defined environment(s), when selected by the learner.

<a name="lms_requirements"></a>  
#6.0 LMS Requirements

LMS systems must meet the following requirements to conform to this specification:  

1. The LMS must implement a LRS as defined in the XAPI Specification.
2. The LMS must implement a means to create and edit course structures as defined in section 6.1 Course structure.
3. The LMS must implement additional “State API” requirements to initialize AU state as defined in section 10.
4. The LMS must implement the runtime launch interface as defined in section 8.0 Content Launch Mechanisms.
5. The LMS must implement additional XAPI “Statement API” requirements as defined in section 9.
6. The LMS must implement additional XAPI “Agent Profile API” requirements as defined in section 11 

<a name="course_structures"></a>  
##6.1 Course structures
The LMS must implement a means to create and maintain course structures.

1. The LMS must implement the import of Course Structures per [CMI5-002] CMI-5 Course Structure
2. The LMS should implement the export of Course Structures per [CMI5-002] CMI-5 Course Structure
3. The LMS should implement a user interface to allow LMS administrative users to create and edit course structures.
4. The LMS must be able support course structures with one or more AU’s

Course structures must contain the following data for each AU in a course:

* URL location – A URL to the AU’s location (entry point)
* Activity ID – the AU’s activity ID as defined in the XAPI specification (determined by the AU designer).
* Launch Method - 
    * “OwnWindow” – The LMS must either spawn a new window for the AU launched, or redirect the existing window to the AU.
    * “AnyWindow” – The AU does not care about the window context (all browser windows options are acceptable – FrameSet, New Window, redirect, etc.) The LMS may use whichever method desired..
* Authentication Method – The authentication method used by the AU to access the LMS’s
LRS.  (Either HTTP basic or OAuth 1.0)
* Launch Parameters –A set of static data specific to the AU’s design. Used as parameters
by the AU to modify its behavior. 
* Entitlement Key – This is a value provided by the AU content provider and is used by the
AU to determine whether the LMS instance and/or Learner are entitled to view the content.
It is provided to the AU via a State API request.

Course Structures must contain at least 1 AU.

LMS must have the ability to create and maintain course structures containing more than
1000 AU’s.

<a name="lms_state_api_requirements"></a>  
##6.2 LMS State API Requirements
The LMS must implement the State API Requirements as defined in section 10.

<a name="lms_statement_api_requirements"></a>  
##6.3 LMS Statement API Requirements
The LMS must implement the Statement API Requirements as defined in section 9.


<a name="au_requirements"></a>  
#7.0 AU Requirements

AU’s must meet the following requirements to conform to this specification:

1. The AU must implement the runtime launch interface as defined in Section 8 Content Launch Mechanisms.
2. The AU must implement runtime communication defined in the xAPI Specification.
3. The AU must implement additional XAPI “Statement API” requirements as defined in section 9.0.
4. The AU must implement additional XAPI “Agent Profile API” requirements as defined in section 11.0.

<a name="au_state_api_requirements"></a> 
##7.1 AU State API Requirements

AU’s must meet the following requirements to conform to this specification:

* The AU must implement additional XAPI “Statement API” requirements as defined in section 9.0 .
* The AU must implement additional XAPI “State API” requirements as defined in section 10.
* The AU must implement additional XAPI “Agent Profile API” requirements as defined in section 11.


<a name="au_statement_api_requirements"></a>  
##7.2 AU Statement API Requirements

<a name="placement"></a> 
###7.2.1 Placement of sessionId in Statements

The AU must retrieve the value of session\_id at launch time as specified in Section 10 State API.  The AU must place the value of the sessionId in the context extensions for all XAPI statements it records.  

Usage in an XAPI Statement:

```javascript
"extensions": {
       “sessionId”: <sessionId value>
     }
```
Example:
```javascript
"extensions": {
       “sessionId”: ”xyz123”
     }
```

<a name="first_statement_au"></a> 
###7.2.2 First Statement API Call
The AU must issue a statement to the LRS after being launched, initialized, and ready for learner interaction using the Initialized verb per section 9.3.2.

<a name="last_statement_au"></a>  
###7.1.2 Last Statement Call
The AU must issue a statement to the LRS prior to termination using the Terminated verb per section 9.3.10.

<a name="content_launch"></a>  
#8.0 Content Launch Mechanisms

<a name="browser_environment"></a>  
##8.1 Web (Browser) Environment

###8.1.1 Launch Method

The AU must be launched by the LMS using one of the following methods, depending on the launchMethod in the Course Structure (Section 7.1.4 AU Meta Data, URL):

When the launchMethod is "OwnWindow", the LMS must use one of the following:
<ol><li>Spawning a new browser window for the AU.</li>
<li>Re-directing the existing browser window to the AU.</li>
</ol>

When the launchMethod is "AnyWindow", the LMS may choose the window context of the AU.  All browser window options are acceptable - Framset, New window, browser redirect, etc.

In either case, the AU must be launched by the LMS with a URL having query string launch parameters as
defined in this section. The launch parameters must be name/value pairs in a query string appended to the URL that
launches the learning activity.

If the learning activity’s URL requires a query string for other purposes, then the names
must not collide with named parameters defined below.

The order of the name/value pairs is not significant. AU’s must have the ability to
process them in any order.

Each value for the associated names must be URL-encoded. 

The format of the launching URL is as follows:  

```
<URL to AU>
?endpoint=<URL to LMS Listener>
&fetch=<Fetch URL for Authorization Token (optional)– if OAuth is not used>
&actor=<Actor Object>
&registration=<Registration ID>
&activityId=<AU activity ID>
```

Example:

```
http://la.cmi5.aicc.org/LA1/Start.html
?endpoint=http://cmi-5-lms-system.org/lrslistner/
&fetch=http://cmi-5-lms-system.org/tokenGen.htm?k=2390289x0
&actor={"objectType": "Agent","account": 
{"homePage": "http://www.example.com","name": "1625378"}
&registration=760e3480-ba55-4991-94b0-01820dbd23a2
&activityId=http://example.AU-content.com/example/001/statement
```

The values for the URL launch parameters are described below: 

<table>
  <tr><th colspan=3 align ="left">endpoint</th></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Description:</th><td>A URL to the LMS listener location for xAPI messages to be sent to.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>LMS Usage:</th><td>LMS must place the <strong><em>endpoint </em></strong>in the query string.<strong></strong>The LMS should limit the use of the <strong><em>auth</em></strong> value for the duration of a specific/user/learning activity/registration</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>AU Usage:</th><td>AU must get the <strong><em>endpoint </em></strong>value from the query string. AU must use the <strong><em>endpoint </em></strong>value as the URL to send xAPI messages to.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Value space:</th><td>An URL-encoded URL</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Sample value:</th><td>https://mylms.aicc.org/MyCMI5_listener.pl</td></tr>
</table>

<table>
  <tr><th colspan=3 align ="left">fetch</th></tr>
  <tr><td>&nbsp;</td><th align ="right">Description:</th><td>The <strong><em>fetch</em></strong> URL is used by the AU to obtain an authentication token created &amp; managed by the LMS.  The <strong><em>fetch</em></strong> URL is only used when OAuth authentication is not practical or desired.  The authentication token is used by the learning activity being launched.</td></tr>
  <tr><td>&nbsp;</td><th align ="right">LMS Usage:</th><td>The LMS must place the <strong><em>fetch</em></strong> in the Launch URL when Basic authentication is indicated in the course structure definition. <br /><br />If OAuth is the method of authentication specified, the LMS must NOT place the <strong><em>fetch</em></strong>name/value pair<strong></strong> in the query string.  <br /><br />The <strong><em>fetch</em></strong> URL is a "one-time use" URL and subsequent uses should generate an error as defined in section 8.2. The authorization token returned by the <strong><em>fetch</em></strong> URL must be limited to the duration of a specific user session. </td></tr>
  <tr><td>&nbsp;</td><th align ="right" >AU Usage:</th><td>When Basic authentication is used, the AU must get the <strong><em>fetch</em></strong> value from the query string. The AU must make an HTTP POST to the <strong><em>fetch</em></strong> URL to retrieve the authorization token as defined in section 8.2. The AU must then place the authorization token in the Authorization headers of all HTTP messages made to the endpoint using the xAPI.  The AU should not make one more than 1 post to the <strong><em>fetch</em></strong> URL</td></tr>
  <tr><td>&nbsp;</td><th align ="right">Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Value space:</th><td>Defined by the LMS</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Sample value:</th><td>http://cmi-5-lms-system.org/tokenGen.htm?k=2390289x0</td></tr>
</table>

<table>
  <tr><th colspan=3 align ="left">actor</th></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Description:</th><td>A JSON object called “actor” (as defined in the XAPI specification) that identifies the learner launching the learning activity so the learning activity will be able to include it in XAPI messages.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>LMS Usage:</th><td>The LMS must place the value for <strong><em>actor </em></strong>in the query string based on the authenticated learner’s identity. The    LMS should create an actor object specific to the LMS instance that does NOT include sensitive PII of the learner.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" >AU Usage:</th><td>AU must get the <strong><em>actor </em></strong>value from the query string. AU must use the <strong><em>actor </em></strong>value in API calls that require an “actor” object when sending XAPI messages</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Value space:</th><td> A JSON Actor object (as defined section 9.2)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Sample value:</th><td>{"objectType": "Agent","account": {"homePage": "http://www.example.com","name": "1625378"}</td></tr>
</table>

<table>
  <tr><th colspan=3 align ="left">registration</th></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Description:</th><td>A Registration ID corresponding to the learner’s enrollment for the AU being launched.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>LMS Usage:</th><td>LMS must place the value for <strong><em>registration</em></strong> in the query string based on the authenticated learner’s corresponding    enrollment for the Course that the AU being launched is a member of.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" >AU Usage:</th><td>AU    must get the <strong><em>registration</em></strong> value from the query string. AU must use the <strong><em>registration</em></strong> value in API calls that require an “registration id” when sending XAPI messages</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Value space:</th><td>UUID (as defined in the XAPI specification)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Sample value:</th><td></td></tr>
</table>

<table>
  <tr><th colspan=3 align ="left">activityId</th></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Description:</th><td>The Activity ID of the AU being launched.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>LMS Usage:</th><td>The LMS must place the value for <strong><em>activityId</em></strong> in the query string based on the definition of the AU in the course    structure.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" >AU Usage:</th><td>AU must get the <strong><em>activityId</em></strong> value from the query string. AU must use the <strong><em>activityId</em></strong> value in API calls that require an “activity id” when sending XAPI messages.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Value space:</th><td>IRI (as defined in the CMI-5 Course Structure section 7.1.4, AU Meta data)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Sample value:</th><td></td></tr>
</table>

<br />
<a name="fetch_url"></a>  
##8.2 Authorization Token Fetch URL
###8.2.1 Overview
When Basic authentication is used, the LMS must include the <strong><em>fetch</em></strong> name/value pair in the launch URL.  The AU must make an HTTP POST to the <strong><em>fetch</em></strong> URL to retrieve an authorization token.  Please note than an HTTP GET is not allowed in order to prevent caching of the request.

The <strong><em>fetch</em></strong> URL must return a JSON structure using a content-type of "application/json".  An example JSON structure is shown below:
```javascript
{
  "auth-token": "QWxhZGRpbjpvcGVuIHNlc2FtZQ=="
}
```
The AU must place the <strong><em>auth-token</em></strong> in the HTTP header, as defined in <a href='http://tools.ietf.org/html/rfc1945#section-11'>RFC 1945 - 11.1 Basic Authentication Scheme</a>, in all subsequent xAPI communications with the LMS.  The authorization token returned by the <strong><em>fetch</em></strong> URL must be limited to the duration of the session.

The AU should not attempt to retrieve the authorization token more than once.  The <strong><em>fetch</em></strong> URL is a "one-time use" URL and subsequent uses should generate an error (see Section 8.2.3). 


###8.2.2 Definition: auth-token
<table>
  <tr><th colspan=3 align ="left">auth-token</th></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Description:</th><td>An authorization token used in all xAPI communications with the LMS when Basic authentication is used.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>LMS Usage:</th><td>The LMS must place the value for <strong><em>auth-token</em></strong> in a JSON structure, as shown in section 8.2.1, in its response to a <strong><em>fetch</em></strong> URL request. The response must have a content-type of "application/json".</td></tr>
  <tr><td>&nbsp;</td><th align ="right" >AU Usage:</th><td>AU must get the <strong><em>auth-token</em></strong> value using an HTTP POST to the <strong><em>fetch</em></strong> URL. The AU must then place the authorization token in the Authorization headers of all HTTP messages made to the endpoint using the xAPI.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Value space:</th><td>Defined by the LMS</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Sample value:</th><td>QWxhZGRpbjpvcGVuIHNlc2FtZQ==</td></tr>
</table>

###8.2.3 Errors
####8.2.3.1 Duplicate call to fetch URL
The <strong><em>fetch</em></strong> URL is a "one-time use" URL and only the first request should return the <strong><em>auth-token</em></strong>. Subsequent requests made to the <strong><em>fetch</em></strong> during the session should generate an error.  The error should be returned in the form of a JSON structure using content-type "application/json".
```javascript
{
  "error-code": "1",
  "error-text": "The authorization token has already been returned."
}
```
####8.2.3.2 Error Values
The following <strong><em>error-code</em></strong> are allowed.
<table>
<tr><td><strong>Code</strong></td><td><strong>Meaning</strong></td></tr>
<tr><td>1</td><td>Already in Use or Expired</td></tr>
<tr><td>2</td><td>General Security Error</td></tr>
<tr><td>3</td><td>General Application Error</td></tr>
</table>

The values for <strong><em>error-text</em></strong> are defined by the LMS.

<br />

<a name="other_environment"></a>  
##8.3 Other Launch Environments

Other launch environments are not currently implemented in this specification. The
following launch environments are being considered for future releases:  

* Windows/XP/7/8 pro  
* Windows RT  
* Mac OS X  
* Linux  
* Android  
* iOS  

CMI-5 implementations for LMS’s and AU’s in these other environments will use the same
REST communication interface as specified in XAPI specification.  The XAPI specification
does not specify launch mechanisms.

<a name="xapi_data_model"/>  
#9.0 XAPI Statement Data Model  

<a name="ID" ></a>
##9.1 Statement ID
The AU will not provide a statement ID for CMI-5 defined statements.  (The LRS will assign statement IDs)  
  
<a name="Actor" ></a>
##9.2 Actor
The Actor object will be defined by the LMS.  The Actor object for all statements with CMI-5 defined verbs must be of type "Agent" and must contain an account object.

Example of usage in a statement:

```javascript
{
  "actor": {
    "objectType": "Agent",
    "account": {
        "homePage": "http://www.example.com",
        "name": "1625378"
   }, 
  "verb": {...},
  "object": {...},
  "result": {...},
  "context": {...},
  "attachments": {...}
}
```

<a name="verbs" ></a> 
##9.3 Verbs  

The following are XAPI verbs that are specific to this specification.

AU’s must use the below verbs indicated as mandatory in other sections of this
specification.

AU’s may use additional verbs not listed in this specification.

LMS system must record and provide reporting for all statements regardless of which verbs
AU’s use in statement.  

###9.3.1 Launched
<table>
<tr><th align="left">Verb</th><td>Launched</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/launched</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Launched" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Launched” indicates that the AU was launched by the LMS.</td>
</tr><tr><th align="left">AU Obligations</th><td>None</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS must use this verb in a statement recorded in the LRS before launching an AU.  (See Statement API section 10) </td></tr>
</tr><tr><th align="left">Usage</th><td>A "Launched" statement is used to indicate that the LMS has launched the AU. It should be used in combination with the "Initialized" statment sent by the AU in a reasonable period of time to determine whether the AU was successfully launched. </td></tr>
</table>

###9.3.2 Initialized
<table>
<tr><th align="left">Verb</th><td>Initialized</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/initialized</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Initialized" }</td></tr>
<tr><th align="left">Description</th><td>A "Initialized" statement is used by the AU to indicate that it has been fully initialized and should follow the "Launched" statement created by the LMS within a reasonable period of time.</td>
</tr><tr><th align="left">AU Obligations</th><td>The AU must use "Initialized" in the first statement in the AU session.</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>Verify that this verb is recorded by AU immediately after launch</td></tr>
</tr><tr><th align="left">Usage</th><td>A "Initialized" statement is used by the AU to indicate that it has been fully initialized and should follow the "Launched" statement created by the LMS within a reasonable period of time.</td></tr>
</table>

###9.3.3 Suspended
<table>
<tr><th align="left">Verb</th><td>Suspended</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/suspended</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Suspended" }</td></tr>
<tr><th align="left">Description</th><td>The learner exited an AU session (uncompleted) with the intention of returning to the AU.</td>
</tr><tr><th align="left">AU Obligations</th><td>The AU must record a statement containing the "Suspended" verb when the learner exits an AU without experiencing all relevant material in the AU.  The AU must not issue a "Suspended" statement if the AU previously issued a statement with "Completed".  After issuing a "Suspended" statement, the AU must issue an "Terminated" statement. The AU must not issue any other statements following "Suspend" except for "Terminated".</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>None.</td></tr>
</tr><tr><th align="left">Usage</th><td>The criterion for "Suspended" is determined by the AU design.</td></tr>
</table>

###9.3.4 Resumed 
<table>
<tr><th align="left">Verb</th><td>Resumed</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/resumed</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Resumed" }</td></tr>
<tr><th align="left">Description</th><td>The learner resumed an AU that was intentionally left uncompleted.</td>
</tr><tr><th align="left">AU Obligations</th><td>The AU must record a statement containing the "Resumed" verb when the learner returns to an AU that had recorded a "Suspend" statement in the previous session.  The AU must record "Resumed" immediately following a the "Initialized" statement. The AU must not issue a "Resumed" statement under any other circumstances.</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>None.</td></tr>
</tr><tr><th align="left">Usage</th><td>See AU Obligations.</td></tr>
</table>


###9.3.5 Completed
<table>
<tr><th align="left">Verb</th><td>Completed</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/completed</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Completed" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Completed” indicates the learner viewed or did all of the relevant activities in an AU presentation.</td>
</tr><tr><th align="left">AU Obligations</th><td>The AU must record a statement containing the "Completed" verb when the learner has experienced all relevant material in an the AU.  The AU must not issue multiple statements with "Completed" for the same AU within a given AU session or course registration for a given learner.</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>None.</td></tr>
</tr><tr><th align="left">Usage</th><td>The criterion for "Completed" is determined by the AU design.</td></tr>
</table>

###9.3.6 Passed
<table>
<tr><th align="left">Verb</th><td>Passed</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/passed</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Passed" }</td></tr>
<tr><th align="left">Description</th><td>The learner attempted and succeed in a judged activity in the AU. </td></tr>
<tr><th align="left">AU Obligations</th><td>The AU must record a statement containing the "Passed" verb when the learner has attempted and passed the AU. The AU must not issue multiple statements with "Passed" for the same AU within a given AU session or course registration for a given learner. If the "Passed" statement contains a (scaled) score, the (scaled) score must be equal to or greater than the "MasteryScore" indicated in the course structure. (See course structure section 7.1.4)</td></tr>
<tr><th align="left">LMS Obligations</th><td>The LMS must record "MasteryScore" data in the state API (if present in the course structure) for the AU prior to initial AU launch. (See section 10) The LMS must use either "Passed" or "Completed" statements (or both) based on the moveOn criteria for the AU as defined in Course Structure. (See Course Structure Section 7.1.4 MoveOn).</td></tr>
<tr><th align="left">Usage</th><td>The AU must record a statement containing the "Passed" verb when the learner has attempted and successfully passed the judged activity. The AU must not issue multiple statements with "Passed" for the same AU within a given AU session or course registration for a given learner. If the "Passed" statement contains a score, the score must equal to or greater than the "MasteryScore" indicated in the course structure. (See Course Structure Section 7.1.4 MasteryScore)</td></tr>
</table>


###9.3.7 Failed
<table>
<tr><th align="left">Verb</th><td>Failed</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/failed</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Failed" }</td></tr>
<tr><th align="left">Description</th><td>The learner attempted and failed in a judged activity in the AU. </td>
</tr><tr><th align="left">AU Obligations</th><td>The AU must record a statement containing the "Failed" verb when the learner has attempted and failed the AU.  If the "Failed" statement contains a score, the score must be less than the "MasteryScore" indicated in the course structure.  (See Course Structure Section 7.1.4 MasteryScore). </td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS must record "MasteryScore" data in the state API (if present in the course structure) for the AU prior to initial AU launch.  (See section 10).<br/>
<br/>
The LMS must use either "Passed" or "Completed" statements (or both) for determining for course completion (or course collateral credit) criteria for the AU.  (See Course Structure Section 7.1.4 MasteryScore).</td></tr>
</tr><tr><th align="left">Usage</th><td>The AU must record a statement containing the "Failed" verb when the learner has attempted and failed the judged activity.. If the "Failed" statement contains a score, the score must be less than the "MasteryScore" indicated in the course structure. (See Course Structure Section 7.1.4 MasteryScore). </td></tr>
</table>


###9.3.8 Abandoned
<table>
<tr><th align="left">Verb</th><td>Abandoned</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/abandoned</td></tr>
<tr><th align="left">Name</th><td>{ "en-US" : "Abandoned" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Abandoned” indicates that the AU session was abnormally terminated by Learner action (or due to a system failure).</td>
</tr><tr><th align="left">AU Obligations</th><td>None.</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS must use the the "Terminated" statement to determine that the AU session has ended.  In the absence of an "Terminated" statement the LMS will make the determination if an AU abnormally terminated a session by monitoring new statement or state API calls made for the same leaner/course registration for a different AU.  The LMS must record an "Abandoned" statement on behalf of the AU indicating an abnormal session termination. </td></tr>
</tr><tr><th align="left">Usage</th><td>See LMS obligations.</td></tr>
</table>



###9.3.9 Waived
<table>
<tr><th align="left">Verb</th><td>Waived</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/waived</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Received Waiver" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Waived” indicates that the LMS has determined that the AU was met by means other than completing the AU.</td>
</tr><tr><th align="left">AU Obligations</th><td>None</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS must use this verb in a statement recorded in the LRS when it determines that the AU may be waived.  A statement containing a Waived verb must include a "reason" in the extension property of the statement Result.  (see section 9.6.2.2) </td></tr>
</tr><tr><th align="left">Usage</th><td>A "Waived" statement is used by the LMS to indicate that the AU may be skipped by the Learner.</td></tr>
</table>



###9.3.10 Terminated
<table>
<tr><th align="left">Verb</th><td>Terminated</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/terminated</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Terminated" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Terminated” indicates that the AU was terminated by the Learner and that the AU will
not be recording any more statements for the launch session.</td>
</tr><tr><th align="left">AU Obligations</th><td>The AU must record a statement containing the "Terminated" verb. This statement must be the last statement recorded by the AU in a session.</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS must use the the "Terminated" statement to determine that the AU session has ended.  In the absence of an "Terminated" statement the LMS will make the determination if an AU abnormally terminated a session by monitoring new statement or state API calls made for the same leaner/course registration for a different AU.  The LMS must record a "Abandoned" statement on behalf of the AU indicating an abnormal session termination per section 9.3.8 Abandoned.</td></tr>
</tr><tr><th align="left">Usage</th><td>See obligations.</td></tr>
</table>

<BR>
<BR>

<a name="Object"></a> 
##9.4 Object 
The Object in a CMI-5 defined statement represents the AU.  An Object must be present as specified in this section in all statements with CMI-5 defined verbs.

<a name="objectType"></a> 
###9.4.1 objectType
The objectType property of an Object in statements with a CMI-5 verb must be set to "activity".

<a name="Object_ID"></a> 
###9.4.2 id 
The value of the Object's ID property for a given AU must match the AU ID defined in the URL launch line and the course structure.

<a name="Definition"></a>
###9.4.3 definition

The object's definition will have the Activity Type contained in the course structure, as defined in section 4.1.4.1 of the XAPI specification, must be included in the "Launched" statement sent from the LMS to the LRS.  This Activity Type
describes the general category of the AU and should be one of the following:

 * http://www.aicc.org/cmi5/activitytypes/assessment
 * http://www.aicc.org/cmi5/activitytypes/tutorial
 * http://www.aicc.org/cmi5/activitytypes/simulation
 * http://www.aicc.org/cmi5/activitytypes/reference
 * http://www.aicc.org/cmi5/activitytypes/jobaid
 * http://www.aicc.org/cmi5/activitytypes/video

Example of usage in a statement:

```javascript
{
  "actor": {...}, 
  "verb": {
               "id": "http://www.aicc.org/cmi5/verbs/launched",   
               "display": {  
                   "en-US": "Launched"
               }
    },
    "object": {
      "id":"<AU identifier>"
      "definition": {          
             "type": "http://www.aicc.org/cmi5/activitytpes/<activity type>",
             "name": {
                     "en-US": "<activity type name>"          
             }
        },
       "objectType": "Activity"       
    },
    "result": {...},
    "context": {...},
    "attachments": {...}
}
```

<table>
<tr><th align="right" nowrap></th><th align="left">Assessment</th></tr>
<tr><th align="right" nowrap>Description: </th><td>An activity  where the learner is evaluated or judged.</td></tr>
<tr><th align="right" nowrap>(definition) type:</th><td>http://www.aicc.org/cmi5/activitytypes/assessment</td></tr>
<tr><th align="right" nowrap>(definition) name:</th><td>{ "en-US" : "assessment" }</td></tr>
</table>

<table>
<tr><th align="right" nowrap></th><th align="left">Tutorial</th></tr>
<tr><th align="right" nowrap>Description: </th><td>An activity the learner is presented material for instruction in a defined sequence</td></tr>
<tr><th align="right" nowrap>(definition) type:</th><td>http://www.aicc.org/cmi5/activitytypes/tutorial</td></tr>
<tr><th align="right" nowrap>(definition) name:</th><td>{ "en-US" : "tutorial" }</td></tr>
</table>

<table>
<tr><th align="right" nowrap></th><th align="left">Simulation</th></tr>
<tr><th align="right" nowrap>Description: </th><td>An activity the learner interacts primarily with a computer-based simulation of system or a physical device</td></tr>
<tr><th align="right" nowrap>(definition) type:</th><td>http://www.aicc.org/cmi5/activitytypes/simulation</td></tr>
<tr><th align="right" nowrap>(definition) name:</th><td>{ "en-US" : "simulation" }</td></tr>
</table>

<table>
<tr><th align="right" nowrap></th><th align="left">Reference</th></tr>
<tr><th align="right" nowrap>Description: </th><td>An activity where the learner can search for and locate information. The presentation of what information to display is learner directed.</td></tr>
<tr><th align="right" nowrap>(definition) type:</th><td>http://www.aicc.org/cmi5/activitytypes/reference</td></tr>
<tr><th align="right" nowrap>(definition) name:</th><td>{ "en-US" : "reference" }</td></tr>
</table>

<table>
<tr><th align="right" nowrap></th><th align="left">Job Aid</th></tr>
<tr><th align="right" nowrap>Description: </th><td>An activity where the learner is using a tool or system that help the learner perform a work related task.</td></tr>
<tr><th align="right" nowrap>(definition) type:</th><td>http://www.aicc.org/cmi5/activitytypes/jobaid</td></tr>
<tr><th align="right" nowrap>(definition) name:</th><td>{ "en-US" : "jobaid" }</td></tr>
</table>

<table>
<tr><th align="right" nowrap></th><th align="left">Video</th></tr>
<tr><th align="right" nowrap>Description: </th><td>An activity where the learner is presented with a video clip as the primary (or only) media presentation.</td></tr>
<tr><th align="right" nowrap>(definition) type:</th><td>http://www.aicc.org/cmi5/activitytypes/video</td></tr>
<tr><th align="right" nowrap>(definition) name:</th><td>{ "en-US" : "video" }</td></tr>
</table>

<a name="Result"></a> 
##9.5 Result
Result may be present in a statement depending on the CMI-5 verb used.  

Example JSON:
```javascript
  "result": {
     "score": {
         "scaled": "0.65",
         "raw": "65",
         "min": "0",
         "max": "100"
     },
     "success": "false",
     "duration": "PT30M",
     "extensions": {
         "http://www.aicc.org/cmi5/extensions/result/progress": "100"
     }
   }
 ```

<a name="Score"></a> 
###9.5.1 Score

A score is not required to be reported.  If a score is reported by an AU, the verb must be consistent with Mastery_Score (if defined for the AU in the course structure).

<ul><li><strong>scaled</strong><br/>A decimal value between 0 and 1.</li>
<li><strong>raw</strong><br/>An integer value between the "min" and "max" properties of the <em><strong>score</strong></em> object.  When the "raw" value is provided, the AU must also provide the "min" and "max" values for <em><strong>score</strong></em>.</li>
<li><strong>min</strong><br/>An integer value indicating the minimum value for the "raw" score property.</li>
<li><strong>max</strong><br/>An integer value indicating the maximum value for the "raw" score property.</li>
</ul>

<a name="Success"></a>
###9.5.2 Success 

The success property of result must be set to true for statements having the following CMI-5 defined verbs:

- Passed
- Waived

The success property of result must be set to false for statements having the following CMI-5 defined verbs:

- Failed
- Abandoned

<a name="Completion"></a>
###9.5.3 Completion
The completion property of result must be set to true for statements having the following CMI-5 defined verbs:

- Completed
- Waived

The completion property of result must be set to false for statements having the following CMI-5 defined verbs:

- Failed
- Abandoned

<a name="Duration"></a>
###9.5.4 Duration
The duration property is a ISO 8601 formatted time value required in certain statements as defined in this section.
####9.5.4.1 AU statements that include duration
##### Terminated Statement
The AU must include the duration property in Terminated statements.  The AU should calculate duration for Terminated statements as the time difference between Initialized statement and the Terminated statement.  The AU may use other methods to calculate the duration based on criteria determined by the AU.
##### Suspended Statement
The AU should include the duration property in Suspended statements.  The AU should calculate duration for Suspended statements as the time difference between Initialized statement and the Suspended statement.  The AU may use other methods to calculate the duration based on criteria determined by the AU.
##### Completed Statement
The AU must include the duration property in Completed statements.  The AU should calculate duration as the time spent by the learner to achieve completion status.
##### Passed Statement
The AU must include the duration property in Passed statements.  The AU should calculate duration as the time spent by the learner to attempt and succeed in a judged activity of the AU. 
##### Failed Statement
The AU must include the duration property in Failed statements. The AU should calculate duration as the time spent by the learner to attempt and fail in a judged activity of the AU.
####9.5.4.2 LMS statements that include duration
##### Abandoned Statement
The duration proprety should be include in Abandoned statements.  The duration property should be set as the total session time, based on the AU launch, as calculated by the LMS.

###9.5.5 Extensions
####9.5.5.1 Progress
An integer value indicating the completion of the AU as a percentage.  The AU may set this value in statements to indicate level of completion between 0 and 100 percent.

<a name="Context"></a> 
##9.6 Context
All statements with CMI-5 defined verbs must contain a context as defined in this section. 

Sample JSON:
```javascript
   "context": {
     "registration": "<registration value provided by LMS>",
     "contextActivities": {
        "category": {[
          {"id": "http://adlnet.gov/CMI5/moveon"},
          {"id": "http://adlnet.gov/CMI5/cmi5"}
        ]}
     },
     "extensions" {
       "sessionId": "<session id provided by the LMS>",
       "reason": "<reason for 'waived' verb, if statement is 'waived' statement only>",
      }
   }
```

<a name="Registration"></a> 
###9.6.1 registration
The value for the registration property used in the context object must be the value provided by the LMS.  The LMS must generate this value and pass it to the AU via the launch line. 

<a name="ContextActivities"></a>
###9.6.2  contextActivities
Statements with a results object (section 9.5) that include either "success” or "completion” properties must contain a contextActivities object with the "id" property of "moveon". Other statements must not include this property. The purpose of this property is to facilitate searches of the LRS by the LMS or other reporting systems.

All CMI5 Statements must include an object with the "id" property of "cmi5" in contextActivities. This purpose of this property is to identify CMI5 specific statements during LRS searches.

<a name="extensions"></a> 
###9.6.3 extensions
The following are extensions specified for CMI-5.  Other extensions are permitted provided they do not conflict or duplicate the ones specified here.  

####9.6.3.1 sessionId

<table>
  <tr><th align ="right" nowrap>ID:</th><td>http://www.aicc.org/cmi-5/extensions/session</td></tr>
  <tr><th align ="right" nowrap>Description:</th><td>An unique identifier for an single AU launch session based on actor and course registration </td></tr>
  <tr><th align ="right" nowrap>LMS Usage:</th><td>The value for Session ID is generated by the LMS. The LMS must also record the Session ID in the State API (per section 10) prior to launching an AU. The LMS must also provide the Session ID in the context as an extension for all Statements (with CMI-5 defined verbs) it makes directly in the LRS.</td></tr>
  <tr><th align ="right" nowrap>AU Usage:</th><td>An AU must include the sessionId provided by the LMS in the context as an extension for all Statements (with CMI-5 defined verbs) it makes directly in the LRS. </td></tr>
 <tr><th align ="right" nowrap>AU Obligation:</th><td>Required</td></tr>
 <tr><th align ="right" nowrap>LMS Obligation:</th><td>Required</td></tr>
  <tr><th align ="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align ="right" nowrap>Value space:</th><td>string value</td></tr>
  <tr><th align ="right" nowrap>Sample value:</th><td></td></tr>
</table>

####9.6.3.2 reason

  <table>
  <tr><th align ="right" nowrap>ID:</th><td>http://www.aicc.org/cmi5/extensions/result/reason</td></tr>
  <tr><th align ="right" nowrap>Description:</th><td>Indicates the reason why an AU was "waived" (marked complete by an alternative means)</td></tr>
  <tr><th align ="right" nowrap>LMS Usage:</th><td>The LMS must set this value in statements it makes with the "Wavied" verb. The value of reason should be one of the following -

<ul>
<li><b>Tested Out</b> – An Assessment was completed by the student to waive the AU.</li>  
<li><b>Equivalent AU</b> The student successfully completed an equivalent AU (in the same course) to waive the AU. </li>  
<li><b>Equivalent Outside Activity</b> – The student successfully completed an equivalent activity outside of the course to waive the AU. </li>    
<li><b>Administrative</b> – The LMS administrative user marked the AU complete.</li> 
</ul>
</td></tr>
  <tr><th align ="right" nowrap>AU Usage:</th><td>The AU may retrieve this value from the LRS and use it to change presentation behavior based on the "reason".</td></tr>
 <tr><th align ="right" nowrap>AU Obligation:</th><td>Optional</td></tr>
 <tr><th align ="right" nowrap>LMS Obligation:</th><td>This is a required extension for LMS statements that include the Waived verb</td></tr>
  <tr><th align ="right" nowrap>Data type:</th><td>String</td></tr>
  <tr><th align ="right" nowrap>Value space:</th><td><ul>
<li>"Tested Out"</li>  
<li>"Equivalent AU"</li>  
<li>"Equivalent Outside Activity"</li>    
<li>"Administrative"</li> 
</ul></td></tr>
  <tr><th align ="right" nowrap>Sample value:</th><td>Tested Out</td></tr>
</table>

<a name="xapi_state"></a>  
#10.0 XAPI State Data Model

Prior to launching a learning activity, the LMS must create a document in the State API record in the 
LRS.  This must be a JSON document as defined in this section with a document name (stateId) of "LMS.LaunchData". The LMS must only create one State document for the combination of activityId, agent, registration, and stateId.  An example of the JSON document is shown below.

```javascript
{
   "contextTemplate": {
         "extensions": {
            "http://www.aicc.org/cmi-5/extensions/session": "<LMS generated sessionId>"
         }
   },
   "launchMode": "<launchMode value>",
   "launchParameters": "<launch parameters from Course Structure>",
   "masteryScore": "<mastery score from the Course Structure>",
   "moveOn": "<moveOn value from the Course Structure>",
   "returnURL": "<URL value>",
   "entitlementKey": {
       "courseStructure": "<Entitlement data or key from Course Structure>",
       "alternate": "<alternateEntitlementKey>"
   }
 }
```

The properties for the LMSLaunchData document are described below.

<table>
  <tr>
    <th align="left">contextTemplate</th>
  </tr> 
<tr>
    <td><p><strong>Description: </strong>Context template for the AU being launched.<br />
      <strong>LMS Required: </strong>Yes<br />
      <strong>AU: Required:</strong> Yes<br />
      <strong>LMS Usage:  </strong>LMS must include a contextTemplate and place the value for <strong><em>sessionId</em></strong> in the "http://www.aicc.org/cmi-5/extensions/session" element
of the context object's extension collection.<br />
      <strong>AU Usage: </strong>AU must get the contextTemplate value from the LMS.LaunchData state document.  The AU must use the contextTemplate as a template for the context property in all xAPI statements it records to the LMS. While the AU may include additional values in the context object of such statements, it must not overwrite any values provided in the contextTemplate. NOTE: this will include the sessionId specified by the LMS.<br />
      <strong>Data type: </strong>JSON context object as defined in xAPI 1.0<br />
      <strong>Value space:</strong> LMS implementation specific<br />
      <strong>Sample value:</strong></p></td>
  </tr>
  <tr>
    <th align="left">launchMode</th>
  </tr> 
<tr>
    <td><p><strong>Description: </strong>The launch mode determined by the LMS. There are three possible values:<br />
      <ul><li>Normal<br/>"Normal" mode indicates to the AU that completion related data must be recorded in the LMS using xAPI statements.</li>
          <li>Browse<br/>"Browse" mode indicates to the AU that completion related data must not be recorded in the LMS using xAPI statements.  When "Browse" mode is used, the AU should provide a user experience that allows the user to "look around" without judgement.</li>
          <li>Review<br/>"Review" mode indicates to the AU that completion related data must not be recorded in the LMS using xAPI statements.  When "Review" mode is used, the AU should provide a user experience that allows the user to "revisit/review" already completed material.</li>
      </ul>
      <strong>LMS Required:</strong> Yes<br />
      <strong>AU Required:</strong> Yes<br />
      <strong>LMS Usage:  </strong>LMS must include a value for <strong><em>launchMode</em></strong>.<br />
      <strong>AU Usage: </strong>The AU must conform to the following based on the value of <strong><em>launchMode</em></strong><br />
      <ul><li>Normal<br/>The AU must record Initialized and Terminated verb statements.  The AU must record other CMI-5 verb statements per the requirements defined in section 9.3 Verbs.</li>
      <li>Browse<br/>The The AU must record Initialized and Terminated verb statements.  The AU must not record other CMI-5 verb statements.</li>
      <li>Review<br/>The The AU must record Initialized and Terminated verb statements.  The AU must not record other CMI-5 verb statements.</li></ul>
      <strong>Data type: </strong>String<br />
      <strong>Value space: </strong>"Normal", "Browse" or "Review"<br />
      <strong>Sample value: </strong>"Normal"</p></td>
  </tr>
    <tr><th align="left">launchParameters</th>
    </tr>
    <tr>
    <tr>
    <td><p><strong>Description: </strong>The launch parameters defined in the CMI-5 Course Structure<br />
      <strong>LMS Required:</strong> If the <strong><em>launchParameters</em></strong> are defined by the AU developer in the Course Structure, the LMS must include the  <strong><em>launchParameters</em></strong> in the State API document.<br />
      <strong>AU Required:</strong> No<br />
      <strong>LMS Usage:</strong> The LMS must include the <strong><em>launchParameters</em></strong> in the State API document when defined in the Course Structure.<br />
      <strong>AU Usage:</strong> AU should get the <strong><em>launchParameters</em></strong> value 
      from the State API document if launch parameters were defined in the Course Structure.<br />
      <strong>Data type:</strong> Defined by AU developer<br />
      <strong>Value space:</strong> Defined by the AU developer<br />
      <strong>Sample value: </strong> TBD</p></td>
  </tr>
  <tr><th align="left">masteryScore</th>
    </tr>
    <tr>
    <tr>
    <td><p><strong>Description: </strong>The MasteryScore from the CMI-5 Course Structure.<br />
      <strong>LMS Required:</strong> Yes<br />
      <strong>AU Required:</strong> Yes<br />
      <strong>LMS Usage:  </strong>The LMS must include the MasteryScore value based on the value defined in the course structure for the AU being launched.<br />
      <strong>AU Usage: </strong>AU must issue Passed or Failed statements based on the MasteryScore provided. (See sections 9.3.6 and 9.3.7)<br />
      <strong>Data type: </strong>decimal<br />
      <strong>Value space: </strong>Decimal value between 0 and 1<br />
      <strong>Sample value: </strong>0.75</p></td>
  </tr>   
  </tr> 
  <tr><th align="left">moveOn</th>
    </tr>
    <tr>
    <tr>
    <td><p><strong>Description: </strong>The moveOn value from the CMI-5 Course Structure.<br />
      <strong>LMS Required:</strong> Yes<br />
      <strong>AU Required:</strong> No<br />
      <strong>LMS Usage:  </strong>The LMS must include the moveOn value defined in the course structure for the AU.<br />
      <strong>AU Usage: </strong>AU may get the moveOn value from the LMS.LaunchData state document and may use the value to modify its behavior.<br />
      <strong>Data type: </strong>string<br />
      <strong>Value space: </strong>moveOn values as defined in CMI-5 Course Structure specification (7.1.4 AU Metadata)<br />
      <strong>Sample value: </strong>"Passed"</p></td>
  </tr>   
    <th align="left">returnURL</th>
  </tr> 
<tr>
    <td><p><strong>Description: </strong>Used by the LMS when launching the AU if the LMS requires the AU (in a web-browser environment) to redirect the learner when they exit the AU.<br />
      <strong>LMS Required:</strong> No<br />
      <strong>AU Required:</strong> If the <strong><em>returnURL</em></strong> is provided.<br />
      <strong>LMS Usage: </strong> LMS may include the <strong><em>returnURL</em></strong> when the learner should be redirected to the <strong><em>returnURL</em></strong> on exiting the course.<br />
      <strong>AU Usage: </strong>AU must get the <strong><em>returnURL</em></strong> value 
      from the LMSLaunchData state document. If the <strong><em>returnURL</em></strong> is provided, the AU must redirect the current browser window to the <strong><em>returnURL</em></strong> when the AU is terminated.<br />
      <strong>Data type: </strong>URL<br />
      <strong>Value space: </strong>Any URL<br />
      <strong>Sample value: </strong>http://www.example.com/lms/mod/xapilaunch/view.php?id=12</p></td>
  </tr>
  <tr>
    <th align="left">entitlementKey: courseStructure</th>
  </tr> 
      <td><p><strong>Description: </strong> Entitlement data or key from the course structure.  The       <strong>EntitlementKey</strong> values may be used by the AU to determine if the launching LMS system is entitled to use the AU.<br />
      <strong>LMS Required: </strong>Yes<br />
      <strong>AU Required: </strong>No<br />
      <strong>LMS Usage:  </strong>The LMS must obtain from the course structure.<br />
      <strong>AU Usage: </strong> The AU should use this data in combination with other data provided from the LMS to determine entitlement.<br />
      <strong>Data type: </strong>string<br />
      <strong>Value space: </strong>The value is defined by the AU provider<br />
      <strong>Sample value: </strong>"xyz-123-9999"</p></td>
  </tr>
  <tr>
    <th align="left">entitlementKey: alternate</th>
  </tr> 
      <td><p><strong>Description: </strong> Entitlement data or key from some other source as agreed upon between the LMS and the AU.  The <strong>EntitlementKey</strong> values may be used by the AU to determine if the launching LMS system is entitled to use the AU.<br />
      <strong>LMS Required: </strong>No<br />
      <strong>AU Required: </strong>No<br />
      <strong>LMS Usage:  </strong>The LMS must obtain the alternate entitlement key from a source as agreed upon with the AU.<br />
      <strong>AU Usage: </strong> The AU should use this data in combination with other data provided from the LMS to determine entitlement.<br />
      <strong>Data type: </strong>string<br />
      <strong>Value space: </strong>The value is defined by the AU provider<br />
      <strong>Sample value: </strong>"xyz-123-9999"</p></td>
  </tr>     
   <tr>
    <th align="left">ContentSpecific</th>
  </tr> 
      <td><p><strong>Description: </strong>Launch parameters that are content specific.  The LMS must obtain this value from the course structure.<br />
      <strong>LMS Required: </strong>Yes<br />
      <strong>AU Required: </strong>No<br />
      <strong>LMS Usage:  </strong>Static launch parameters defined by the AU designer must be obtained by the LMS from the course structure.<br />
      <strong>AU Usage: </strong>Determined by the AU<br />
      <strong>Data type: </strong>string<br />
      <strong>Value space: </strong>Values are defined by the AU provider<br />
      <strong>Sample value: </strong>"abc-327-999"</p></td>
  </tr>      
</table>

__State API PUT Properties__:

* _activityId_: Activity ID for the AU (from the course structure)  
* _agent_: agent representing the LMS learner being enrolled.  This must match actor object
generated by LMS at AU launch time.  
* _registration_: Registration ID representing the LMS learner enrollment in the course.
This must match Registration ID used by the LMS at AU launch time.  
* _stateId_: LMS.LaunchData  



<a name="xapi_agent_profile"></a>   
#11.0 XAPI Agent Profile Data Model  

In CMI5, Learner Preferences are scoped to the learner.  Both the LMS and the AU may write changes to Learner Preferences in the xAPI Agent Profile.  The LMS/LRS may choose to ignore or "override" Learner Preference changes requested by the AU by returning a "403 Forbidden" response as defined in the xAPI specification (section 7.6).  The AU must not treat the 403 response as an error condition.  

On startup an AU must retrieve the Learner Preferences document from the Agent Profile.

When reading or writing to the Agent Profile, the document name must be CMI5LearnerPreferences and the format must be a JSON structure as shown below:

```javascript
{
	"languagePreference": "<values for languages>",
	"audioPreference": "<on or off>"
}
```
##11.1  languagePreference
This must be a comma-separated list of RFC 5646 Language Tags as indicated in the xAPI specification (section 5.2).  In the list, languages must be specified in order of user preference.  In the example below, the user's first preference for language is en-US.  The user's second preference for language is fr-FR and the third preference is fr-BE.

```javascript
{
	"languagePreference": "en-US,fr-FR,fr-BE",
	...
}
```

The AU should display in the language preference order of the user if the AU supports multiple languages.  In the example above, if the AU supported "zh-CN", "fr-BE and "fr-FR", it should display in "fr-FR".  If the AU does not support multiple languages, or if no languagePreference is specified in the Agent Profile, it may display in its default language.

##11.2 audioPreference
The audioPrefence value indicates whether the audio should be "on" or "off".  The AU must turn the audio on or off at startup based on this value.  If no value is provided in the Agent Profile for audioPreference the AU may use its own default value.

Example:
```javascript
{
	"audioPreference": "on",
	...
}
```


<a name="xapi_activity_profile"></a>  
#12.0 XAPI Activity Profile Data Model

The AU may use the Activity Profile API per the xAPI specification (section 7.5 Activity Profile API).

<a name="bibliography"></a>   
#Bibliography

[1]  AICC CMI001, CMI Guidelines For Interoperability, Version 4.0. 

[2]  SCORM – <http://www.adlnet.gov/capabilities/scorm>

[3]  MIME Types – <http://www.iana.org/assignments/media-types/index.html>

[4]  RFC 2396, “Uniform Resource Identifiers (URI): Generic Syntax,” August 1998.

[5]  Experience API, Version 1.0.1, ADL, 2012-2013 - <https://github.com/adlnet/xAPI-Spec/blob/master/xAPI.md>

[6]  CMI5-002 – LMS Course Structure, current working draft, AICC, 2013 -  
<https://github.com/AICC/CMI-5_Spec_Current/blob/master/cmi5_coursestructure.md>


-------

<a id="license_agreement"></a> 
#License Agreement

THE WORK (AS DEFINED HEREIN) ACCOMPANYING THIS LICENSE AGREEMENT ("AGREEMENT") IS PROVIDED
BY THE AICC, A NON-PROFIT CORPORATION ORGANIZED UNDER THE LAWS OF Idaho (“LICENSOR”), TO
YOU (“YOU” OR “LICENSEE”) ONLY UNDER THE TERMS AND CONDITIONS OF THIS AGREEMENT. ANY USE,
REPRODUCTION, DISTRIBUTION OR MODIFICATION OF THE WORK BY YOU CONSTITUTES YOUR ACCEPTANCE
OF THIS AGREEMENT. BY OBTAINING, USING, DISTRIBUTING, REPRODUCING AND/OR MODIFYING THE
WORK, YOU AGREE THAT YOU HAVE READ, UNDERSTOOD, AND WILL COMPLY WITH THE FOLLOWING TERMS
AND CONDITIONS.

####1. DEFINITIONS

“Affiliate” means any entity that directly or indirectly controls, is controlled by, or is
under common control with, another entity, so long as such control exists. For purposes of
this definition, with respect to a business entity, “control” means a majority vote of
voting members.  In the event that such control ceases to exist, any grant of rights or
other contractual powers granted to such Affiliate hereunder will be immediately
withdrawn, and this Agreement as between Licensor and such Affiliate shall be terminated
as set forth in Section 9, below.

“Compliance Test Suite” means any suite of computer programs (e.g., test tools), database
schema, plans, procedures, checklists, documentation and the like developed or adopted by
or for AICC and approved by AICC for the purpose of determining the compliance of an
implementation of a Specification.

“Contribution” means a submission by Licensee or Other Licensee to Licensor in writing
(including a writing in electronic medium) of a change, modification or addition to the
Work for inclusion in future versions of the Work; and which such submission is accepted
for inclusion in the Work by Licensor. Contributions do not include additions to the Work
that: (i) are separate works distributed in conjunction with the Work under their own
license agreement, and (ii) are not Derivative Works of the Work.

“Contributor” means any Licensee or any Other Licensee person or entity that submits a
Contribution.

“Derivative Work” is as defined in the United States Copyright Act 17 U.S.C. § 101, and
means any document, standard, specification, computer program, compilation, technical
data, schema, XML instance document or similar work that includes or derives from major
elements of the Work, whereby such major elements are protected by copyright, patent or
any other recognized intellectual property right.

“AICC” means the Aviation Industry Computer Based Training Committee Corporation, a
non-profit corporation organized under the laws of Idaho.

“Licensee” means you as a party to this Agreement to include all your Affiliates.

“Necessary Claims” means those claims of all patents and patent applications throughout
the world, other than design patents and design registrations, whereby such claims are
necessarily infringed by an implementation of a Work and which are within the bounds of
the Scope, where such infringement could not have been avoided by another commercially
feasible non-infringing implementation of such Work. Necessary Claims do not include any
claims (i) other than those set forth above even if contained in the same patent as
Necessary Claims or (ii) that read solely on an optional implementation example or
optional reference implementation.

“Other Licensee” or “Other Licensees” means a third party licensee (or licensees) other
than you, whereby such third party licensee has separately entered into this Agreement
with Licensor, to include all Affiliates of such third party licensee.

“Scope” means the software interfaces disclosed with particularity in a Specification
where the sole purpose of such disclosure is to enable products to interoperate,
interconnect or communicate as defined within a Specification. Notwithstanding the
foregoing, the Scope shall not include (i) any enabling technologies that may be necessary
to make or use any product or portion thereof that complies with a Specification, but are
not themselves expressly set forth in a Specification (e.g., compiler technology, object
oriented technology, basic operating system technology); (ii) the implementation of other
published specifications not developed by or for AICC, but referred to in the body of a
Specification; or (iii) any portions of any product and any combinations thereof the
purpose or function of which is not required for compliance with a Specification.

“Specification” means a document entitled “Specification” or “Standard” adopted and
approved for release by AICC relating to any AICC implementation, and any updates or
revisions adopted and approved for release.

“Standards Organization” means any entity whose primary activities are developing,
coordinating, promulgating, revising, amending, reissuing, interpreting, or otherwise
maintaining standards that address the interests of a wide base of users or consumers of
such standards outside the standards development organization.

“Technical Note” means a proposal, document or guide, other than a Specification, which
has been approved for release as a AICC Technical Note. Typically, a Technical Note will
contain functional and technical information to aid in the implementation of a
Specification as adopted and approved for release by AICC.

“Work” means any Specification, Technical Note or Compliance Test Suite distributed in
accordance with and licensed under this Agreement.

####2. LICENSE GRANT AND RESTRICTIONS

a. Subject to the terms of this Agreement, Licensor hereby grants to Licensee a
non-exclusive, worldwide, royalty-free license in any copyrights and/or Necessary Claims
in the Work such that Licensee may view, use, reproduce, publicly display, distribute and
prepare Derivative Works of the Work. 

b. Licensee hereby grants to Licensor and all Other Licensees a non-exclusive, worldwide,
royalty- free license in any copyrights and/or Necessary Claims in which Licensee asserts
ownership, such that Licensor and all Other Licensees may view, use, reproduce, publicly
display, distribute and prepare Derivative Works of any Contributions that Licensee may
have made to the Work. Licensee agrees that it will not transfer its ownership of any
copyrights or patents having Necessary Claims for the purpose of circumventing this
Section 2.b. Licensee shall not attempt under its copyrights, Necessary Claims or
otherwise to restrict any Other Licensee from exercising that Other Licensee’s rights
granted to it by Licensor under an agreement with essentially the same terms and
conditions as this Agreement. 

c. To the extent that a Licensee reproduces or distributes copies of the Work, portions
thereof or any Derivative Work in any medium, with or without modifications, such Licensee
shall give a copy of this Agreement to any recipients of the Work. 

d. Licensee hereunder expressly agrees to include the following notice on ALL copies of
the Work, portions thereof or Derivative Works: "Copyright © The AICC. All Rights
Reserved.  <http://www.aicc.org>” 

e. Licensee agrees to include the following notice in all Derivative Works:
“This product implements and complies with the Version CMI-5 [or other version as
applicable] AICC Specifications as published by the AICC at <http://www.aicc.org>”. 

f. Licensee may not facilitate or assist any Learning Technology Standards Organization
other than Licensor in co-opting, copying, distributing, publishing or using the Work
without prior written approval of Licensor. Licensee may not create any Derivative Work
for ownership by, presentation by, distributing by, publishing by or attribution to any
Standards Organization or similar entity other than Licensor, unless specifically approved
in writing by Licensor. 


####3. GRANT OF RIGHTS BY CONTRIBUTORS
Subject to the terms of this Agreement, a Contributor hereby grants to Licensor a
non-exclusive, worldwide, royalty-free license under all intellectual property rights to
make, use, sell, offer to sell, import and otherwise transfer any Contribution of such
Contributor. This license shall apply to the combination of the Contribution and the Work.

####4. TRADEMARKS
This Agreement does not grant permission to use the trade names, trademarks, service
marks, or product names of the Licensor, except as required for reasonable and customary
use in describing the origin of the Work and reproducing the content of the copyright
notice.

####5. WARRANTY
THE WORK ACCOMPANYING THIS AGREEMENT IS PROVIDED "AS IS" WITHOUT WARRANTIES OR CONDITIONS
OF ANY KIND, AND THE HOLDERS OF ANY COPYRIGHT, PATENT OR OTHER INTELLECTUAL PROPERTY RIGHT
THEREIN MAKE NO REPRESENTATIONS OR WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT
LIMITED TO, WARRANTIES OF MERCHANTABILITY OR FITNESS FOR ANY PARTICULAR PURPOSE OR THAT
THE USE OF THE SOFTWARE OR DOCUMENTATION WILL NOT INFRINGE ANY THIRD PARTY PATENTS,
COPYRIGHTS, TRADEMARKS OR OTHER RIGHTS. You are solely responsible for determining the
appropriateness of using or redistributing the Work and assume any risks associated with
your exercise of permissions under this Agreement.

####6. LIMITATION OF LIABILITY
IN NO EVENT AND UNDER NO LEGAL THEORY, WHETHER IN TORT (INCLUDING NEGLIGENCE), CONTRACT,
OR OTHERWISE, UNLESS REQUIRED BY APPLICABLE LAW (SUCH AS DELIBERATE AND GROSSLY NEGLIGENT
ACTS) OR AGREED TO IN WRITING, SHALL LICENSOR OR ANY CONTRIBUTOR BE LIABLE TO YOU FOR ANY
DAMAGES WHATSOEVER, INCLUDING ANY DIRECT, INDIRECT, EXEMPLARY, PUNITIVE, SPECIAL,
INCIDENTAL, OR CONSEQUENTIAL DAMAGES OF ANY CHARACTER ARISING AS A RESULT OF THIS
AGREEMENT OR OUT OF THE USE OR INABILITY TO USE THE WORK (INCLUDING BUT NOT LIMITED TO
DAMAGES FOR LOSS OF PROFITS, GOODWILL, WORK STOPPAGE, COMPUTER FAILURE OR MALFUNCTION, OR
ANY AND ALL OTHER COMMERCIAL DAMAGES OR LOSSES), EVEN IF LICENSOR OR SUCH CONTRIBUTOR HAS
BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.

####7. COMMERCIAL DISTRIBUTION
If you include the Work or any Derivative Work in a commercial product offering, you
hereby agree to defend and indemnify Licensor and every Contributor (the "Indemnitees ")
against any losses, damages and costs (collectively "Losses") arising from claims,
lawsuits and other legal actions brought by a third party against the Indemnitees, to the
extent caused by your acts or omissions in connection with your distribution of the Work
in a commercial product offering. Indemnitees shall: a) promptly notify you in writing of
such claim, and b) allow you to control, and cooperate with you in, the defense and any
related settlement negotiations. Any Indemnitee may participate in any such claim at its
own expense.

####8. PROPRIETARY RIGHTS
Regardless of who owns the media on which the Work resides or is distributed, the Work
expressly remains the intellectual property of Licensor and/or the Contributors, and
Licensor and/or the Contributors retain all right, title and interest in and to the Work
and all copies thereof. Licensor expressly reserves all rights not specifically granted in
this Agreement.

####9. TERMINATION
Licensor reserves the right to terminate this Agreement at any time if you are in breach
of any of its terms and conditions, copyright laws, or any other applicable laws or
regulations. In such a case, the rights granted to you under Section 2 of this Agreement
shall be automatically terminated, and you shall be obliged to cease using the Work and
immediately destroy any copies of the Work and all backup copies. Termination is not the
sole remedy under this Agreement and, whether or not termination is effected, all other
remedies, legal and equitable, will remain available.

####10. UPGRADES
Licensor is under no obligation under this Agreement to provide any fixes, revisions,
upgrades or future versions of the Work to you or to any other party. Should you ever
obtain an upgrade of this Work, the terms and conditions of this Agreement shall also
apply to the upgrade. The Work is subject to change without notice.

####11. GENERAL

a. Independent Contractors. The parties and their respective personnel are and shall be 
independent contractors and neither party by virtue of this Agreement shall have any
right, power or authority to act or create any obligation, express or implied, on behalf
of the other party. 

b. Binding Nature. Subject to all other provisions herein contained, this Agreement shall
be binding on the parties and their successors and permitted assigns. 

c. Assignment. Licensee may not assign or otherwise transfer this Agreement, or any part
hereof, nor delegate any of its duties hereunder, whether by operation of law or
otherwise, to any third party. Licensee may delegate specific duties and obligations
hereunder to an Affiliate, however, in the event that Licensee wishes to assign or
transfer this entire Agreement to an Affiliate, Licensee may do so only via a novation
whereby all parties agree to such novation in writing and the Affiliate in effect becomes
the Licensee hereunder. 

d. Severability. If any provision of this Agreement is found by a court of competent
jurisdiction to be invalid or unenforceable, such invalidity or unenforceability shall
not invalidate or render unenforceable any other part of this Agreement, but the Agreement
shall be construed as not containing the particular provision or provisions held to be
invalid or unenforceable. 

e. Waiver. No delay or omission by either party hereto to exercise any right occurring
upon any noncompliance or default by the other party with respect to any of the terms of
this Agreement shall impair any such right or power or be construed to be a waiver
thereof. A waiver by either of the parties hereto of any of the covenants, conditions or
agreements to be performed by the other shall not be construed to be a waiver of any
succeeding breach thereof or of any covenant, condition or agreement herein contained. 

f. Governing Law; Exclusive Jurisdiction. This Agreement, and all the rights and duties of
the parties arising from or relating in any way to the subject matter of this Agreement or
the transaction(s) contemplated by it, shall be governed by, construed and enforced in
accordance with the law of the State of Idaho (excluding any conflict of laws provisions
of the State of Idaho that would refer to and apply the substantive laws of another
jurisdiction). Any suit or proceeding relating to this Agreement shall be brought in the
state courts of Idaho. Each of the parties consents to the exclusive personal jurisdiction
and venue of the state courts located in Idaho. 

g. No Construction Against Drafter. The parties agree that any principle of construction
or rule of law that provides that an agreement shall be construed against the drafter of
the agreement in the event of any inconsistency or ambiguity in such agreement shall not
apply to the terms and conditions of this Agreement. 

h. Entire Agreement; Modification. This Agreement sets forth the entire, final and
exclusive agreement between the parties as to the subject matter hereof and supersedes
all prior and contemporaneous agreements, understandings, negotiations and discussions,
whether oral or written, between the parties. The parties expressly disclaim the right to
claim the enforceability or effectiveness of any other amendments that are based on course
of dealing, waiver, reliance, estoppel or other similar legal theory. The parties
expressly disclaim the right to enforce any rule of law that is contrary to the terms of
this section. 
	
i. Survival. The following sections shall survive any termination of this Agreement: 2.c,
2.d, 2.e, 2.f, 4, 5, 6, 7, 8 and 11.a.


-------
