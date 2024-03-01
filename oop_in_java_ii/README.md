Object-Oriented Programming with Java (Part II)
Issue Tracker 🐛

The goal of this exercise is to apply what you've learned from the second lecture on OOP - abstract classes, interfaces, enums, and exceptions.

We will create a bug tracking and software project management system similar to JIRA.

The main components are the following classes:

Jira Class

Implements the interfaces:

public interface Filter {
    public Issue find(String issueID);
}

public interface Repository {
    public void addIssue(Issue issue);
}


It has a constructor without parameters:

public Jira();

As well as the methods:

public void addActionToIssue(Issue issue, WorkAction action, String actionDescription) {}
public void resolveIssue(Issue issue, IssueResolution resolution) {}
It can store up to 100 issues at once. If this limit is exceeded or an attempt is made to add an issue that has already been added (criteria for equality is the unique ID of the issue), throwan appropriate exception.

Issue Class

It has the following methods:

public String getIssueID() { return null; }
public String getDescription() { return null; }
public IssuePriority getPriority() { return null; }
public IssueResolution getResolution() { return null; }
public IssueStatus getStatus() { return null; }
public Component getComponent() { return null; }
public LocalDateTime getCreatedOn() { return null; }
public LocalDateTime getLastModifiedOn() { return null; }
public String[] getActionLog(){ return null; }

public void setStatus(IssueStatus status) {}
public void addAction(WorkAction action, String description) {}

public abstract void resolve(IssueResolution resolution);


The constructor declaration should look like this:

public Issue(IssuePriority priority, Component component, String description) {}

It has at least the following fields:

Unique ID - formed from the short name of the component + a unique number that increases by 1 with each creation of an issue (e.g., FMI-666; starts from 0)
Description - a brief description of the problem it solves
Priority - can be TRIVIAL, MINOR, MAJOR, CRITICAL
Resolution - how the issue was resolved. Can be FIXED, WONT_FIX, DUPLICATE, CANNOT_REPRODUCE, UNRESOLVED. Upon creation, the status is UNRESOLVED by default
Status - can be OPEN, IN_PROGRESS, RESOLVED. Upon creation, the status is OPEN by default
Component to which the issue belongs
Action log - keeps a list of actions performed by the programmer while working on the issue. Actions can be RESEARCH, DESIGN, IMPLEMENTATION, TESTS, FIX
The list consists of strings in the format <action>: <description>. For example, "fix: Added 'products.manage' scope check in authorizer". The description of the action is mandatory.

It can store up to 20 actions. If this limit is exceeded, throw an appropriate exception.

The moment (timestamp) of creation
When it was last modified over time


Task Class

The Task class inherits from Issue. It is used for short-term tasks that are usually not related to writing code.

The characteristic of this class is that it cannot accept the actions Fix, Implementation, and Tests in its action log since they are characteristic of another type of issues.
When attempting to add such an action, an appropriate exception should be thrown.

Feature Class

Inherits from Issue. Represents the task that a programmer receives when working on adding new functionality to the component they are working on.

These types of tasks cannot be resolved if the mandatory actions Design, Implementation, and Tests have not been added. When attempting to resolve them without adding one of these mandatory actions, an appropriate exception should be thrown.

Bug Class

Such a task is given to the programmer who has to fix part of already existing code.

Again, it inherits the abstract class Issue. A bug cannot be resolved until the Fix and Tests actions are performed. When attempting to resolve it without adding one of these mandatory actions, an appropriate exception should be thrown.

Component Class

It has the following constructor:

public Component(String name, String shortName);
We consider two components equal if they have the same names (name) and abbreviations (shortName).

Notes:

In this task, the use of arrays only is allowed since we have not yet become familiar with collections.
Your project must have the following structure:

src
  ╷
  └─ bg/sofia/uni/fmi/mjt/jira/
    ├─ Jira.java
    ├─ issues/
    |   ├─ Issue.java
    |   ├─ Task.java
    |   ├─ Feature.java
    |   ├─ Bug.java
    |   ├─ Component.java
    |   └─(...)
    |
    ├─ interfaces/
    | ├─ Filter.java
    | ├─ Repository.java
    | └─ (...)
    |
    └─ enums/
      ├─ IssuePriority.java
      ├─ IssueResolution.java
      ├─ IssueStatus.java
      ├─ WorkAction.java
      └─ (...)
When you are ready, upload a zip archive of the src directory of your project to sapera.org.
