---
layout: single
title: Add/Remove operation is impossible, the code element 'Cxxx' is read only
date: 2009-05-12 09:15
categories: Development
tags: bug faq programing vs9
---
<p>&#160;</p>  <p>When attempting to add a Control Event Handler to a control on a dialog, we are encountering the message: Add/Remove operation is impossible, the code element 'Cxxx' is read only. </p>  <p>After an hour of trying to solve it my self, a quick Google search turned up the following solutions. </p>  <ul>   <li>Add random charters to the .h/.cpp file</li>    <li>clean your solution </li>    <li>Close all open windows and close the project. </li>    <li>Delete .ncb and .suo files </li>    <li>Open your project solution and rebuild </li>    <li>Attempt to add your new control event handler. </li> </ul>  <p>This seemed to work for me with </p>  <blockquote>   <p>Microsoft Visual studios 2009     <br />Version 9.0.21022.8 RTM</p> </blockquote>  <p>Source: <a href="http://connect.microsoft.com/VisualStudio/feedback/ViewFeedback.aspx?FeedbackID=99076">http://connect.microsoft.com/VisualStudio/feedback/ViewFeedback.aspx?FeedbackID=99076</a></p>
