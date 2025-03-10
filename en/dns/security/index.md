---
title: Access management in {{ dns-full-name }}
description: "Access management in the service for managing DNS zones and domain names of your resources — {{ dns-full-name }}. The section describes which resources you can assign a role to, which roles operate in the service, which roles are required for this or that action."
---

# Access management

In this section, you'll learn:
* [Which resources you can assign roles to](#resources).
* [Which roles exist in the service](#roles-list).
* [Which roles are required](#required-roles) for particular actions.

{% include [about-access-management](../../_includes/iam/about-access-management.md) %}

## What resources you can assign roles to {#resources}

{% include [basic-resources](../../_includes/iam/basic-resources-for-access-control.md) %}

## What roles exist in the service {#roles-list}

The diagram shows which roles are available in the service and how they inherit each other's permissions. `dns.editor`, for instance, includes all the permissions of `dns.viewer`. A description of each role is given under the diagram.

![image](../../_assets/dns/security/service-roles-hierarchy.svg)

Active roles in the service:

* Service roles:
   * {% include [dns.viewer](../../_includes/iam/roles/dns-viewer-short.md) %}
   * {% include [dns.editor](../../_includes/iam/roles/dns-editor-short.md) %}
   * {% include [dns.admin](../../_includes/iam/roles/dns-admin-short.md) %}

* Primitive roles:
   * {% include [viewer](../../_includes/iam/roles/short-descriptions/viewer.md) %}
   * {% include [editor](../../_includes/iam/roles/short-descriptions/editor.md) %}
   * {% include [admin](../../_includes/iam/roles/short-descriptions/admin.md) %}

## What roles do I need {#required-roles}

The table below lists the roles needed to perform a given action. You can always assign a role granting more permissions than the role specified. For example, assign `editor` Instead of `viewer` or `dns.admin` Instead of `dns.editor`.

| Action | Methods | Required roles |
|:----------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **View data** |                                                                   |                                                                                                                                                                            |
| View information about any resource | `get`, `list` | `viewer` or `dns.viewer` for the resource in question |
| **Manage DNS zones** |                                                                   |                                                                                                                                                                            |
| Create a zone | `create` | `editor` or `dns.editor` for the folder as well as `vpc.user` for the folder and the VPC network if it is an internal zone |
| Edit and delete zones | `update`, `delete` | `editor` or `dns.editor` for the folder as well as `vpc.user` for the folder and the VPC network if it is an internal zone |
| Creating subzones | `create` | `editor` or `dns.editor` for the folder housing the zone that will include the subzones being created as well as `vpc.user` for this folder or VPC network if it is an internal zone |
| **Manage resource records** |                                                                   |                                                                                                                                                                            |
| Create resource records in a DNS zone | `create` | `editor` or `dns.editor` for the folder or zone |
| Edit and delete resource records | `update`, `delete` | `editor` or `dns.editor` |
| **Manage access to DNS zones** |                                                                   |                                                                                                                                                                            |
| [Grant a role](../../iam/operations/roles/grant.md), [revoke a role](../../iam/operations/roles/revoke.md), and view roles granted for DNS zones | `setAccessBindings`, `updateAccessBindings`, `listAccessBindings` | `admin` or `dns.admin` for the folder or zone |

To restrict user access, assign users roles for individual zones or subzones.

#### What's next {#next}

* [How to assign a role](../../iam/operations/roles/grant.md).
* [How to revoke a role](../../iam/operations/roles/revoke.md).
* [Learn more about access management in {{ yandex-cloud }}](../../iam/concepts/access-control/index.md).
* [More information on inheriting roles](../../resource-manager/concepts/resources-hierarchy.md#access-rights-inheritance).
