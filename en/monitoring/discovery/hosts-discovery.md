---
id: hosts-discovery
title: Hosts Discovery
---

> To be updated

![image](../../assets/monitoring/discovery/host-discovery.gif)

> The discovery providers are provided from installation of Plugin Packs (Azure,
> Amazon AWS, VMware, etc.). To know the complete list, please go to
> the [Plugin Packs
> catalog](../../integrations/plugin-packs/introduction.html).

## Add a discovery job

To launch a discovery, you need to add a discovery job.

The job addition wizard is a six steps wizard that will allow you to choose a
provider, define parameters, define mapping rules and update/execution
policies.

Go to `Configuration > Hosts > Discovery` and click on **+ADD**.

### Choose a provider

First, choose a provider by clicking on it:

![image](../../assets/monitoring/discovery/host-discovery-wizard-step-1-1.png)

The search bar allows to search for a specific provider:

![image](../../assets/monitoring/discovery/host-discovery-wizard-step-1-2.png)

A job name can be defined to identify it. The provider name will be used by
default.

### Define access and discovery parameters

The second step allows to define access parameters, especially the monitoring
server from which the discovery will be made:

![image](../../assets/monitoring/discovery/host-discovery-wizard-step-2.png)

Then, some additional parameters might be needed to define the scope of the
discovery:

![image](../../assets/monitoring/discovery/host-discovery-wizard-step-3.png)

### Set mappers

The fourth step defines how the discovery result will be processed to create
hosts in the configuration.

In this step, *mappers* can be added or rearranged to match needs. See the
[How to use the *mappers*](#how-to-use-the-mappers) chapter to know more.

Realtime simulation on a set of example data gives a preview of what the
discovery result could look like:

![image](../../assets/monitoring/discovery/host-discovery-wizard-step-4.png)

### Define analysis and update policies

The fifth step allows to choose between two analysis methods and define
configuration update policies.

#### Manual analysis

Manual analysis will need user to choose what to add to the configuration
through the result page after the job successfully finish.

#### Automatic analysis

Automatic analysis will process the result automatically and will use the
choosen policies between the following:

  - Add hosts to configuration when they are discovered for the first time
  - Disable hosts already added to configuration if the mapping rule excludes
    them
  - Enable hosts already added to configuration if they are discovered but
    disabled

![image](../../assets/monitoring/discovery/host-discovery-wizard-step-5-2.png)

> At least one of these policies must be selected.

### Plan execution

The last step allows to choose between two execution methods.

#### Execute immediately

The immediate execution will launch the discovery right after the job creation.

#### Schedule execution

The scheduled execution allows to choose between several types of scheduling:

  - Every year at defined days of defined months and defined time

![image](../../assets/monitoring/discovery/host-discovery-wizard-step-6-year.png)

  - Every month at defined days of the month and defined time

![image](../../assets/monitoring/discovery/host-discovery-wizard-step-6-month.png)

  - Every week at defined days of the week and defined time

![image](../../assets/monitoring/discovery/host-discovery-wizard-step-6-week.png)

  - Every day at defined time

![image](../../assets/monitoring/discovery/host-discovery-wizard-step-6-day.png)

  - Every x hours (at defined minutes)

![image](../../assets/monitoring/discovery/host-discovery-wizard-step-6-hour.png)

  - Every x minutes

![image](../../assets/monitoring/discovery/host-discovery-wizard-step-6-minute.png)

Click on **FINISH** to add and execute or schedule the discovery job.

## Manage discovery jobs

Go to the `Configuration > Hosts > Discovery` menu to access to the list of
discovery jobs.

![image](../../assets/monitoring/discovery/host-discovery-job-listing.png)

The status of a job can be:

  - Scheduled <img src="../../assets/monitoring/discovery/host-discovery-scheduled.png" width="25" />
  - Running <img src="../../assets/monitoring/discovery/host-discovery-running.png" width="25" />
  - Saving <img src="../../assets/monitoring/discovery/host-discovery-saving.png" width="25" />
  - Finished <img src="../../assets/monitoring/discovery/host-discovery-finished.png" width="25" />
  - Failed <img src="../../assets/monitoring/discovery/host-discovery-failed.png" width="25" />

If a job is on a *Failed* status, hover on to the icon to know the reason.

If a job is on a *Finished* status, click on it to analyse the result. See
[Analyse a discovery job result](#analyse-a-discovery-job-result) to know more.

Jobs can be re-executed using the *Force execution* action <img src="../../assets/monitoring/discovery/host-discovery-force-execution.png" width="40" />

They can also be edited <img src="../../assets/monitoring/discovery/host-discovery-edit.png" width="40" /> 

Or even deleted <img src="../../assets/monitoring/discovery/host-discovery-delete.png" width="40" />

If the job is scheduled, it can be paused <img src="../../assets/monitoring/discovery/host-discovery-pause.png" width="40" />

And resumed <img src="../../assets/monitoring/discovery/host-discovery-resume.png" width="40" />

## Analyse a discovery job result

From the `Configuration > Hosts > Discovery` menu, click on a *Finished* job to
visualize the result.

![image](../../assets/monitoring/discovery/host-discovery-hosts-listing.png)

The mappers linked to this job can be edited and applied directly on the result
by clicking the edit action <img src="../../assets/monitoring/discovery/host-discovery-hosts-edit-mappers" width="40" />

Select the hosts you want to add to the configuration and click on the save
action <img src="../../assets/monitoring/discovery/host-discovery-hosts-save" width="40" />

A task will be launched in background to save the hosts.

Go to the `Configuration > Hosts` menu to see the newly created hosts. To
deploy the services link to the host template, select the hosts and choose
**Deploy Service** from the **More actions...** drop-down menu.

![image](../../assets/monitoring/discovery/host-discovery-configuration-hosts.png)

If the hosts you selected are not visible in the configuration, go back to the
job listing and see if an error occured during the saving task.

## Edit a discovery job

From the `Configuration > Hosts > Discovery` menu, click on the *Edit* action.

![image](../../assets/monitoring/discovery/host-discovery-edit-job.png)

On the panel on the right, every parameters of the job can be edited.

Edition of the *mapper* will have a direct effect on the job result.

Click on the *Save* icon <img src="../../assets/monitoring/discovery/host-discovery-save.png" width="50" />

## How to use the *mappers*

A *mapper* is an object letting you map an attribute's value of a discovered
item to a property of a future host.

There is six types of *mappers*:

  - Association: map an attribute's value to a common host property like name,
    alias or IP,
  - Macro: map an attribute's value to a host custom macro,
  - Template: add a host template,
  - Monitoring: choose from which monitoring server will be monitored the host,
  - Exclusion: exclude a subset of hosts based on their attributs,
  - Inclusion: include a subset of hosts that may be excluded.

For all those *mappers*, conditions can be applied to choose whether or not the
mapping will actually occur.

Conditions are also based on attributes value to which a user defined value is
compared using operators. Operators can be : equal, not equal, contain and not
contain.

![image](../../assets/monitoring/discovery/host-discovery-mappers-condition.png)

The list of attributes depends on the provider and are listed as *Source* for
both *mappers* and conditions.

### Add a *mapper*

From the job wizard at step four, or from the edition panel in the *Mappers*
section, click on **+ADD MAPPER**.

Select the type of *mapper* from the drop-down list, and fill every required
fields.

Click on **SAVE** to add the *mapper*.

### Edit a *mapper*

From the job wizard at step four, or from the edition panel in the *Mappers*
section, click on the *Edit* icon <img src="../../assets/monitoring/discovery/host-discovery-edit.png" width="25" />

Change any fields wanted or even the type of *mapper*.

Click on **SAVE** to save the *mapper*.

### Delete a *mapper*

From the job wizard at step four, or from the edition panel in the *Mappers*
section, click on the *Delete* icon <img src="../../assets/monitoring/discovery/host-discovery-delete.png" width="25" />

A popin window will ask you to confirm the action.

Click on **DELETE** to delete the *mapper*.

## *Mappers* types

### Association

The **Association** *mapper* is used to set common properties of a host like
its name, alias or IP address. Those three properties are mandatory.

![image](../../assets/monitoring/discovery/host-discovery-mappers-association.png)

The *Source* listing allows to choose between credentials, parameters or
discovery result attributes.

The *Destination* listing allows to define to which property the value will be
mapped.

### Macro

The **Macro** *mapper* is used to create custom macros to be defined on the
host.

![image](../../assets/monitoring/discovery/host-discovery-mappers-macro.png)

The *Source* listing allows to choose between credentials, parameters or
discovery result attributes.

The *Destination* is a user defined text field.

The *Password* checkbox defines if the macro will be created as a password
macro or not.

### Template

The **Template** *mapper* is used to add a template to the host. It is not a
replace method.

![image](../../assets/monitoring/discovery/host-discovery-mappers-template.png)

The *Host template* listing allows to choose among all host templates defined
in the configuration.

### Monitoring

The **Monitoring** *mapper* is used to choose from which monitoring server will
be monitored the host.

![image](../../assets/monitoring/discovery/host-discovery-mappers-monitoring.png)

The *Monitoring instance selector* radio buttons allow to choose between the
monitoring server defined in the job or from the ones available on the
Centreon platform.

This *mapper* is mandatory.

### Exclusion

The **Exclusion** *mapper* is used to exclude a subset of hosts from the result
listing.

![image](../../assets/monitoring/discovery/host-discovery-mappers-exclusion.png)

The mapper uses hosts attributs as conditions to exclude them.

### Inclusion

The **Inclusion** *mapper* is used to include a subset of hosts to the result
listing.

![image](../../assets/monitoring/discovery/host-discovery-mappers-inclusion.png)

The mapper uses hosts attributs as conditions to include them.
