---
layout: post
title: "Integrating Jira with MCP in Cursor: A Practical Example"
date: 2024-04-03 11:30:00 -0400
categories: [Development, Tools]
tags: [jira, cursor, mcp, automation, productivity]
---

One of the powerful features of Cursor is its ability to interact with Jira through the MCP (Multi-Command Protocol) server. In this post, I'll walk you through a real example of how I used this integration to manage a development task from start to finish.

## The Task: Adding a Menu Bar

I started with a Jira ticket (AIB-1) that required adding a menu bar to display links to the four most recent blog posts and a link to view all posts. Here's what the initial ticket looked like:

![Initial Jira Ticket]({{ site.baseurl }}/assets/images/jira-ticket-initial.png)

The ticket was in the "To Do" status and assigned to me. Using Cursor's MCP integration, I was able to:
1. View the ticket details
2. Implement the required changes
3. Update the ticket status
4. Add detailed comments about the implementation

## Implementing the Solution

After implementing the menu bar feature (which included creating a custom header and an "All Posts" page), I used Cursor's MCP commands to:

1. Check the current ticket status:
```
mcp_mcp_atlassian_jira_get_issue AIB-1
```

2. Get available status transitions:
```
mcp_mcp_atlassian_jira_get_transitions AIB-1
```

3. Update the ticket status to "Done" with a detailed comment:
```
mcp_mcp_atlassian_jira_transition_issue AIB-1 31 "Completed implementation..."
```

## The Result

After the implementation and status update, the ticket was successfully moved to "Done" with a detailed comment tracking all the changes made:

![Updated Jira Ticket]({{ site.baseurl }}/assets/images/jira-ticket-done.png)

The comment included:
- Created custom header with latest posts section
- Added "All Posts" page with complete post listing
- Implemented responsive design
- Added proper styling matching the site theme
- Changes committed and pushed to repository (commit: 5bce37a)

## Benefits of MCP Integration

This integration between Cursor and Jira through MCP offers several advantages:

1. **Seamless Workflow**: No need to switch between your IDE and browser to update Jira tickets
2. **Detailed Tracking**: Easy to add comprehensive comments with implementation details
3. **Version Control Integration**: Ability to reference commit hashes in ticket updates
4. **Status Management**: Simple transition between ticket statuses
5. **Time Efficiency**: Reduced context switching while working on tasks

## Available Jira Commands

Some useful Jira commands available through MCP in Cursor include:

- `jira_search`: Search for issues using JQL
- `jira_get_issue`: Get detailed information about a specific issue
- `jira_get_transitions`: View available status transitions
- `jira_transition_issue`: Update issue status
- `jira_add_comment`: Add comments to issues
- `jira_create_issue`: Create new issues
- `jira_update_issue`: Update existing issues

## Conclusion

The integration between Cursor and Jira through MCP significantly streamlines the development workflow. It allows developers to manage their tasks, update tickets, and track progress without leaving their IDE. This not only saves time but also encourages better documentation and tracking of development work.

In future posts, I'll explore more advanced features of the MCP integration and share additional productivity tips for using Cursor effectively in your development workflow. 