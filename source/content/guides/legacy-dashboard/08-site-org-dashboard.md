---
title: Legacy Dashboard
subtitle: Managing Sites and Teams with the Pantheon Organization Dashboard
description: Detailed information on how to add users and sites to your organization.
tags: [agencies, collaborate, dashboard, organizations, teams]
contributors: [whitneymeredith]
showtoc: true
reviewed: "2022-08-20"
permalink: docs/guides/legacy-dashboard/org-dashboard
editpath: legacy-dashboard/08-site-org-dashboard.md
contenttype: [guide]
innav: [false]
categories: [organizations, dashboard]
cms: [wordpress, drupal]
audience: [agency, business]
product: [dashboard]
integration: [--]
---

The Organization Dashboard is where Organization Administrators and Team Members manage all their sites in a single location. If you are an Administrator or Team Member for your Organization, you can access support requests, add or remove organizational team members, and manage new or existing sites.

<Alert title="For Info on the New Dashboard" type="info">

This document refers to the Legacy Dashboard. Visit the [New Pantheon Dashboard Workspaces guide](/guides/new-dashboard/workspaces) for information on teams and professional workspaces in the New Pantheon Dashboard.

</Alert>

## Add Sites to Your Organization

### New Sites

While creating a new site, the **Organization Affiliation** field that lists the organizations to which a user belongs, is displayed to any user in your [organization](/guides/account-mgmt/workspace-sites-teams/workspaces). New sites that are affiliated with an organization are automatically added to your Organization Dashboard, and the user who creates the site is designated as the owner.

### Existing Sites

From the Site Dashboard, the Site Owner will want to:

<Alert title="Note" type="info">

Because Supporting Organizations have full access to a site, only the site owner can perform this action.

</Alert>

1. Navigate to the [Pantheon Site Dashboard](https://dashboard.pantheon.io/) > click <span class="glyphicons glyphicons-group"></span> **Team** in the upper-right corner.

1. Click <span class="glyphicons glyphicons-plus-sign"></span> **Add Supporting Organization** at the bottom of the Manage Team window.

  ![Add a supporting organization button](../../../images/dashboard/multi_org1.png)

1. Enter the agency's full name > click **Search**. 

  Use the [Agency Directory](https://directory.pantheon.io/agencies?docs) to search Agency Partners or to be matched with the right Partner. Note that the name must match exactly.

1. Click the **Add** button after you've located and confirmed the correct agency.

  ![Confirm supporting organization](../../../images/dashboard/multi_org2.png)

  The agency will receive an email notification.

<Alert title="Note" type="info">

 If your Organization is Enterprise, EDU+, or a Reseller, you will need to [contact support](/guides/support/contact-support/) to transfer sites to your Organization.

</Alert>

## Manage Site Teams

If you need to add developers as full team members to a site, or outside contractors to individual sites, the Organization Administrator or existing Site Team Member will need to add them to the site team:

1. Check the box next to the site or sites you want to add the user to.
2. Click **Team** and **Add a team member**.
3. Enter the user's email address.
4. Click **Add team member**.

The user will receive an email notification with a link to the Site Dashboard.

Removing site team members follows the same process.

## Filter Sites

At the Sites tab, the left panel contains groups of filters for limiting the sites list. Filters will appear in each group as sites are added that match the filters.

### Site Plan

This lets you filter sites by their [site plan](/guides/account-mgmt/plans).

### Tags

You can add custom tags by selecting the checkbox next to the site, and clicking **Tags** and **Add Tag(s)**, then entering the tag.

<Alert title="Note" type="info">

Tags are case-sensitive.

</Alert>

To remove tags, select the site(s) you want to remove and follow the procedure above, this time selecting **Remove Tag**, or by hovering over the tag and clicking the **x** that appears.

### Upstream

Use this filter to sort sites by their upstream. This includes both [Pantheon upstreams](/start-state/#pantheon-upstreams) and [Custom Upstreams](/guides/custom-upstream).

### Code Status

This filter shows which sites have core updates available, which ones are up to date, and which ones are unknown (e.g., managed by Composer). At this time, Organizations with over 800 sites do not have access to this filter, as they will time out loading.

### Status

This filter shows any sites that are [frozen](/guides/platform-considerations/platform-site-info#inactive-site-freezing), or awaiting upgrade to the [Global CDN](/guides/global-cdn).

### User in Charge

Filters sites by the [user in charge](/guides/account-mgmt/workspace-sites-teams/teams/#roles-and-permissions).

## Add Users to Your Organization

Organization Administrators can add members to the Organization Team as follows:

1. Click on the **People tab**.
2. Click **Add user**.
3. Enter the user's email address.
4. Choose the user's role.
5. Click **Add user**.

If the person does not yet have a Pantheon account, they will receive an email with an invitation to create one. Once they have successfully created an account, they will be automatically added to the Organization. If they already have an account, they will receive an email with a link to the Organization's dashboard.