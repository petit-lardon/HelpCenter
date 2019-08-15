# Bridge v2

[&#8672; *Table of contents*](/helpCenter/)

**Usefull links:**

- [Bridge Back Office Preprod](https://bridge.c.leadformance.com/)
- [Bitbucket Repositories](https://bitbucket.org/dashboard/repositories)
- [Bridge Components Library](https://github.com/Leadformance/bridge-template-components)
- [Bridge Component Repo](http://leadformance.github.io/bridge-template-doc/#/?t=1%23components%2Fform%2Fcontact%2Fbasic.html)
- [Documentation Liquid](https://shopify.github.io/liquid/)
- [Zendesk](https://leadformance.zendesk.com)

## Environment installation

Follow the [Leadformance Documentation](https://documentation.leadformance.com/frontend/Starter-Kit%20V2/Installation/MacOS/Environment/).

## Retrieve the project

### Clone the repository from Bitbucket

```bash
git clone git@bitbucket.org:leadformance/project_name.git
```

### Get the API Key

1. Browse [Bridge Back Office](https://bridge.c.leadformance.com/)
2. Select the client in the upper left corner
3. *Control Panel* > *Company Settings* > *API Keys*
4. Copy the `write_templates` key

### Get the template name

1. Browse [Bridge Back Office](https://bridge.c.leadformance.com/)
2. *Control Panel* > *Superadmin*
3. Click on the client name
4. *Templates*
5. Look for the template used for the front office you need

### Retrieve the template

```bash
cd project_name
nvm use 6.13.1
yo bridge-template
```

> If the project have template folders you need to be in the one you want

Paste the API Key when it's asked, then select the template.

:warning: *Stop the process before `npm install`*

```bash
nvm use 0.12.7
npm install
```

## Update your modifications

```bash
nvm use 0.12.7
grunt upload
```

This command update the preprod website directly.

> If there is error lint you can't fix, you can force the process with `grunt upload --force`.

To get the url of the preprod website:

1. Browse [Bridge Back Office](https://bridge.c.leadformance.com/)
2. Select the client in the upper left corner
3. *Control Panel* > *Implementation Settings*
4. Look for the front office you need

## Update the repository on Bitbuket

1. Create your own branch
2. Commit on this new branch
3. Merge it into master
4. Push the master branch
