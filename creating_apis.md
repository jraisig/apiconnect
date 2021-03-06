---

copyright:
  years: 2017
lastupdated: "2017-08-03"

---


{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Creating APIs
{: #creating_apis}

You can create APIs by downloading the developer toolkit and by using the command line
interface (CLI) or API Designer.

## The developer toolkit CLI
{: #dev_tk_cli notoc}

The developer toolkit provides a command line interface that you can use to publish APIs to
{{site.data.keyword.apiconnect_long}}.
You publish APIs by including them in a Product and then publishing the Product. You define your
APIs and Products by creating and validating YAML definition files in your local file system. You
can then interact with {{site.data.keyword.apiconnect_long}} by
using the toolkit commands.

## API Designer
{: #designer notoc}

The API Designer is an offline graphical user interface within the developer toolkit and provides
functions for the creation and configuration of APIs.
The API Designer is run by using the edit command from the command line interface. When the edit
command is used, the API Designer opens in your default browser or can be accessed through the local
host port that is displayed when you run the command.

## Installing the developer toolkit
{: #install_dev_tk}

### Prerequisites

Before you begin, You must install [Node.js](https://nodejs.org/en/) on the machine on which
you want to use the toolkit, and ensure that `node` is in your `PATH`.

The following items are installed when you install the developer toolkit.

- {{site.data.keyword.apiconnect_short}} command line tool
- {{site.data.keyword.apiconnect_short}} graphical editor
- Local {{site.data.keyword.apiconnect_short}} Micro-gateway


1. To install the toolkit, open your command prompt as administrator and enter the following
command.

    ```
    npm install -g apiconnect
    ```
    {: codeblock}

    **Note:** During installation, you might see errors from the `node-gyp` module. These
    errors are from an optional dependency and the installation will complete successfully.

2. To view summary usage help for all the toolkit commands, enter the following command:

    ```
    apic
    ```
	{: codeblock}

3. To view usage help for any command, use the `--help` option.
    For example:

    ```
    apic validate --help
    ```
	{: codeblock}
	
## Installing LoopBack connectors
{: #install_lb_conn}

Before you can use a LoopBack data source to access data in a backend system such as a
database, you must install the data source connector. The In-memory and email connectors are built
in to LoopBack, so you don't need to install them.

### Prerequisites

The Oracle, DB2, and SQLLite connectors require C compiler tools to build and install binary
extensions. The exact requirements depend on your operating system as described in the following
table.

<table summary="" id="apic_028__table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>Table 1. Operating system-specific installation requirements</caption>
<thead>
<tr>
<th style="width: 33.3%" id="d70e208" class="thleft style-scope doc-content">Windows</th>
<th style="width: 33.3%" id="d70e210" class="thleft style-scope doc-content">Linux</th>
<th style="width: 33.3%" id="d70e212" class="thleft style-scope doc-content">MAC OS X</th>
</tr>
</thead>
<tbody >
<tr class="style-scope doc-content doc-tr-odd">
<td style="width: 33.3%" ><a href="https://www.microsoft.com/en-us/download/details.aspx?id=17851" rel="external" target="blank" title="(Opens in a new tab or window)" >Microsoft .NET Framework 4</a></td>
<td style="width: 33.3%">Python v2.7 (v3.x is not supported)</td>
<td style="width: 33.3%" ><a href="https://www.python.org/downloads/mac-osx/" rel="external" target="blank" title="(Opens in a new tab or window)" >Python
Releases for Mac OS X</a></td>
</tr>
<tr><td style="width: 33.3%" ><a href="https://www.visualstudio.com/downloads/download-visual-studio-vs" rel="external" target="blank" title="(Opens in a new tab or window)" >Visual Studio</a></td>
<td style="width: 33.3%">
<code>make</code>
</td>
<td style="width: 33.3%" ><a href="https://developer.apple.com/xcode/?cm_mc_uid=46449280653414622613810&amp;cm_mc_sid_50200000=1459433716" rel="external" target="blank" title="(Opens in a new tab or window)" >Xcode</a></td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" ><a href="https://www.python.org/downloads/release/python-2710/" rel="external" target="blank" title="(Opens in a new tab or window)" >Python v2.7.10</a></td>
<td style="width: 33.3%">A C/C++ compiler toolchain, for example GCC version 4.2 or later. </td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr><td style="width: 33.3%" ><a href="https://www.microsoft.com/en-gb/download/details.aspx?id=8279" rel="external" target="blank" title="(Opens in a new tab or window)" >Microsoft Windows SDK for Windows 7</a></td>
<td style="width: 33.3%">On Debian and Debian-derived distributions (Ubuntu, Mint etc), use the command:
<pre class="codeblock style-scope doc-content"><code>apt-get install build-essential</code></pre>
</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 33.3%" >npm version 3. See the following note.</td>
<td style="width: 33.3%">&nbsp;</td>
<td style="width: 33.3%" >&nbsp;</td>
</tr>
</tbody>
</table>

**Note:** For Windows installations:

- Use Visual Studio Community unless you want to purchase Visual Studio Enterprise. Run the
installer, check "Visual C++" under "Programming Languages", and accept the default installation
location.

- For 64-bit builds of Node.js and native modules, you also need the Windows&trade; 7 64-bit SDK. If the installation fails, try uninstalling any C++ 2010
x64&amp;x86 redistributable that you have installed first. If you get errors that the 64-bit
compilers are not installed, you might also need the compiler update for the Windows&trade; SDK 7.1.
- Enter the following command to install npm version 3:
  ```
  npm install -g npm
  ```
  {: codeblock}
  Then ensure that the npm command uses the correct version:
  ```
  npm -v
  ```
  {: codeblock}
  If the version shown is not 3.x.x, then edit your system PATH to ensure that `C:\Users\username\AppData\Roaming\npm` supersedes any other entries.


1. **Optional**:
If you are using the API Designer, open a new shell window.

2. When you have installed the compiler tools that are required for your operating system, install
the connector by entering the following command in the project root directory.

```
npm install --save <connector-package>
```
{: codeblock}
where `<connector-package>` is the name of the npm package for the LoopBack connector, as shown in the table.

<table summary="" id="apic_connectors_table_pre_reqs" class="defaultstyle style-scope doc-content">
<caption>Table 3. LoopBack Connectors</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="d70e1489" class="thleft style-scope doc-content">Data source</th>
<th style="width: 50%" id="d70e1491" class="thleft style-scope doc-content">Connector Package</th>
</tr>
</thead>
<tbody>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Cloudant</td>
<td style="width: 50%">loopback-connector-cloudant</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DashDB</td>
<td style="width: 50%">loopback-connector-dashdb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">DB2</td>
<td style="width: 50%">loopback-connector-db2</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 for zOS</td>
<td style="width: 50%">loopback-connector-db2z</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft SQL Server</td>
<td style="width: 50%">loopback-connector-mssql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">MongoDB</td>
<td style="width: 50%">loopback-connector-mongodb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">MySQL</td>
<td style="width: 50%">loopback-connector-mysql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Oracle</td>
<td style="width: 50%">loopback-connector-oracle</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">PostgreSQL</td>
<td style="width: 50%">loopback-connector-postgresql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">SOAP web services</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">REST web services</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

## Creating a LoopBack API by using the CLI
{: #create_lb_api}

The following procedure describes how to create a LoopBack&reg; API by using the command line interface.


### Prerequisites

Before you begin, have the catalog
identifier for the catalog that you want to use to hand. To get the catalog identifier, complete the
following steps:

1. Go to the {{site.data.keyword.apiconnect_short}} **Dashboard**.

2. For the catalog that you want to use, click the **Show catalog identifier** 
icon <img alt="Chain link icon to display the catalog identifier" src="images/chain_link_icon.png">.

3. Copy the catalog identifier. For example:
```
apic config:set catalog=apic-catalog://<region>.apiconnect.ibmcloud.com/orgs/<username_string>-dev/catalogs/<catalog>
```
{: codeblock}

    where:

    - `<region>` is the {{site.data.keyword.Bluemix_short}} region.

    - `<username_string>` is your {{site.data.keyword.Bluemix_short}} org ID without any symbols. For example,
    `joe@mycompany.com` would be `joemycompanycom`

    - `<catalog>` is the name of your catalog

To create a LoopBack API by using the CLI, complete the following steps:

1. To create a project, open a command line and enter:
  ```
  apic loopback
  ```
  {: codeblock}

2. In the prompt that follows, you are asked to name your application. Type a name then press
**Enter**.
  ```
  ? What's the name of your application? (<application name>)
  ```
    
    The tool prompts you to enter the name of the directory in which to create the
    project.
    ```
    ? Enter name of the directory to contain the project: (<project directory name>)
    ```
    
3. Press **Enter** to use the name you previously entered or type a new name then press **Enter**. The tool prompts you to select the kind of application to
create:
```
? What kind of application do you have in mind? (Use arrow keys)
  empty-server (An empty LoopBack API, without any configured models or datasources)
> hello-world (A project containing a basic working example, including a memory database)
```

4. Select the application that you want to use and press **Enter**.
The tool displays a number of messages as it creates the project directory and adds a
number of directories and files to it.It also runs `npm install` to
install all the project dependencies, as specified in `package.json`.
This process might take some time.

5. Before you can create a model, you need to make sure that your current working directory is the
project top-level directory. To do this, enter the following command:
    ```
    cd <project directory name>
    ```
    {: codeblock}

6. To create a model, enter the following command:
    ```
    apic create --type model
    ```
    {: codeblock}

    The tool prompts you for the name of the model.

    ```
    ? Enter the model name:
    ```

7. Enter a name for the model.
    In general, you can use any alphanumeric characters plus dashes and underscores in a model
    name.
    All the data sources that you added to the project are listed and the tool prompts you
    to select a data source to
    use:
    ```
    ? Select the data-source to attach item to: (Use arrow keys)
    ```

8. Select the data source that you want to use and press **Enter**. The tool prompts you to select the model's base
class:
    ```
    ? Select model's base class (Use arrow keys)
       Model
    < PersistedModel
      ACL
      AccessToken
      Application
      Change
      Checkpoint
    (Move up and down to reveal more choices)
    ```
    For more information about each option, see [Using built-in models](https://loopback.io/doc/en/lb3/Using-built-in-models.html).

9. Select a base class and press **Enter**. The tool asks whether you want to expose the model's REST
API.
```
? Expose branch via the REST API? (Y/n)
```
If the model is exposed over REST,
then all the standard create, read, update, and delete operations are available via REST
endpoints.

10. Enter your selection and press **Enter**.
If you chose to expose the model over REST, the tool prompts you for the plural form of
the model name.
```
? Custom plural form (used to build REST URL):
```

11. Press **Enter** to use the default standard English rules for
pluralization.
The tool prompts whether you want to create a server-only model, or a common model that
can be used in both server or client LoopBack&reg;
API.
```
? Common model or server only? (Use arrow keys)
```

12. Use the arrow keys to make your selection and press **Enter**.
The tool prompts you to add properties to the model:
```
Let's add some branch properties now.
Enter an empty property name when done.
? Property name:
```

13. Enter a property name.
The tool prompts you to select the data type of the
property:
```
? Property type: (Use arrow keys)
> string
  number
  boolean
  object
  array
  date
  buffer
```

14. Select the string type and press **Enter**.
The tool asks whether the property is
required:
```
? Required? (y/N)
```

15. Type `y` or `n` then press
**Enter**.
The tool prompts you to add another
property:
```
Let's add another branch property.
Enter an empty property name when done.
? Property name:
```

16. If required, add another property name. If you do not require any more properties press
**Enter** to finish adding the model.

By default, a LoopBack&reg; project comes configured with an in-memory data source, suitable for development and testing. However, at some point you'll want to connect your models to a real data source such as database server. Complete the following steps to add a data source:

1. Enter the following command:
```
apic create --type datasource
```
{: codeblock}
The tool prompts you for the name of the data source.
```
? Enter the data-source name:
```

2. Enter a name for the data source.  You can use any alphanumeric character, dashes, and underscores in a data source
name. The tool prompts you to select the connector to use for the data source:
```
? Select the connector for myds: (Use arrow keys)
> In-memory db (supported by StrongLoop)
  Email (supported by StrongLoop)
  MySQL (supported by StrongLoop)
  PostgreSQL (supported by StrongLoop)
  Oracle (supported by StrongLoop)
  Microsoft SQL (supported by StrongLoop)
  MongoDB (supported by StrongLoop)
(Move up and down to reveal more choices)
```

3. Use the arrow keys to select the connector that you want to use, then press
**Enter**.
The tool then adds the data source to the project.

4. Enter your host, port, user, password, and database credentials.
The tool prompts you to install the LoopBack&reg; connector.
```
Install loopback-connector-<connector>?
```

5. Type `Yes`.
The tool installs the connector.

NOTE: If you selected the Oracle connector, you must set an environment variable in
{{site.data.keyword.Bluemix_short}} for the Oracle app to start. To
do this, complete the following steps:

1. In the {{site.data.keyword.Bluemix_short}} UI, select
**Compute**.

2. In CF Applications, select the application that you want to work with.

3. Click **Runtime**.

4. Select **Environment Variables**.

5. In the User-Defined section, click **ADD**.

6. In the **Name** field, enter `LD_LIBRARY_PATH`.

7. In the **Value** field, enter
`$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`.

8. Click **Save**.

### Testing a LoopBack project
{: #test_lb_proj}

To test a LoopBack&reg; project, complete the following steps.

1. **Optional**: Make sure that your current working directory is the project top-level directory. Enter the
following command:
```
cd <loopback-project-dir>
```
where `<loopback-project-dir>` is the name of the directory that contains the project.
2. Enter the following command:
```
apic start
```
This runs the LoopBack&reg; project (API) and the Micro Gateway locally. The following messages are displayed:
```
Waiting for loopback-project to complete deployment.
Waiting for loopback-project-gw to complete deployment.
Service loopback-project (id 1) started on port 4001
Service loopback-project-gw (id 2) started on port 4002
```
where: `<loopback-project>` is the name of the directory that
contains the project.

You can then test any of the API endpoints by using `curl`, for example.
If you want to load the API by using a web browser, open
`http://localhost:4001` in your browser. For the default LoopBack&reg; (empty or hello-world) project, you see something like this:
```
{"started":"2016-03-07T22:24:55.322Z","uptime":35.839}
```

### Publishing a LoopBack application to Bluemix from the CLI
{: #pub_lb_app_cli}

To publish a LoopBack application to {{site.data.keyword.Bluemix_short}} from the command line, complete the following steps:

1. Enter the following command to ensure that you are in the Loopback project directory.
```
cd <loopback-project-dir>
```
2. Enter the following command to log in to {{site.data.keyword.apiconnect_short}} and {{site.data.keyword.Bluemix_short}}.
```
apic login --server  <region>.apiconnect.ibmcloud.com -u <username> -p <password>
```
where:
  * `<username>` is your {{site.data.keyword.apiconnect_short}} org ID.
  * `<password>` is your {{site.data.keyword.apiconnect_short}} password.
3. Press the space bar to automatically open the **One time passcode** browser page.
4. Click **Regenerate** and copy the one time passcode.
5. Back in the CLI, paste the passcode to complete your login. The following message is displayed:
```
Logged into <region>.apiconnect.ibmcloud.com successfully
```
6. Enter the following command:
```
apic organizations -s <region>.apiconnect.ibmcloud.com
```
where:
  * `<region>` is the {{site.data.keyword.Bluemix_short}} region. For example:
  * `eu` if you are using {{site.data.keyword.Bluemix_short}} London.
  * `us` if you are using {{site.data.keyword.Bluemix_short}} Dallas.
  * `au` if you are using {{site.data.keyword.Bluemix_short}} Sydney.

  If you are unsure, you can locate your region by clicking the {{site.data.keyword.avatar}} icon <img src="images/i-avatar-icon.svg" alt="avatar icon"/> in the menu bar to open the Account and Support widget and check the region field.
7. Enter the following command to publish your application to {{site.data.keyword.Bluemix_short}}.
```
apic apps:publish –a <app> -o <org> -s <region>.apiconnect.ibmcloud.com
```
where:
  * `<app>` is the name of your app
  * `<org>` is the name of your {{site.data.keyword.Bluemix_short}} organization
  * `<region>` is the {{site.data.keyword.Bluemix_short}} region
The following output is returned:
  ```
  ...preparing project
  ...building package for deploy
  ...uploading package
  Runtime published successfully.
  Management URL: https://new-console.stage1.ng.bluemix.net/apps/3aa7087d-b454-4e13-bbc5-8228ebe00eef
  API target urls: apiconnect-3aa7087d-b454-4e13-bbc5-8228ebe00eef.pszetousibmcom-dev.apic.stage1.mybluemix.net
  API invoke tls-profile: client:Loopback-client
  ```

8. Next, you must modify the Product definitions with the values that are returned during the publish time. To do this complete the following steps:

    1. In the API Designer UI, click **APIs**.
    2. Select your API.
    3. Click **Assemble**.
    4. In the Assembly editor, click the **Filter policies** icon.
    5. Select **DataPower Gateway policies**.
    6. Double-click **invoke**.
    7. Update the following fields with the values you retrieved in step 7.
        - **Invoke URL**: Insert the API target URL. You must specify the secure protocol HTTPS. For
        example:
        ```
        https://apiconnect-33e7b062-092b-4227-af97-047499dab2e7.<Bluemix org>-<Bluemix space>.apic.<domain name>$(request.path)
        ```
        If you did not make a note of this value, you can retrieve by going to the management URL returned in
        step 7. You can also retrieve it by logging in to {{site.data.keyword.Bluemix_short}} and viewing your app information.
        - **TLS Profile**: Insert the API invoke tls-profile. For example:
        ```
        client:Loopback-client
        ```
    8. Click **Save** to save the API.

## Creating a LoopBack API by using the API Designer
{: #create_lb_api_design}

The following procedure describes how to create a LoopBack&reg; API by using the API Designer.
{:shortdesc}

### Prerequisites

**Note**: The following instructions assume that you are using the latest version of
the developer toolkit. To check the latest version, see the [npm](https://www.npmjs.com/package/apiconnect) package page.

First, you need to create a LoopBack&reg; project using the CLI. Complete the following steps to do this:

1. To create a project, open a command line and enter:
  ```
  apic loopback
  ```
  {: codeblock}

2. In the prompt that follows, you are asked to name your application. Type a name then press
**Enter**.
  ```
  ? What's the name of your application? (<application name>)
  ```
    
    The tool prompts you to enter the name of the directory in which to create the
    project.
    ```
    ? Enter name of the directory to contain the project: (<project directory name>)
    ```
    
3. Press **Enter** to use the name you previously entered or type a new name then press **Enter**. The tool prompts you to select the kind of application to
create:
```
? What kind of application do you have in mind? (Use arrow keys)
  empty-server (An empty LoopBack API, without any configured models or datasources)
> hello-world (A project containing a basic working example, including a memory database)
```

4. Select the application that you want to use and press **Enter**.
The tool displays a number of messages as it creates the project directory and adds a
number of directories and files to it.It also runs `npm install` to
install all the project dependencies, as specified in `package.json`.
This process might take some time.

5. Before you can create a model you need to make sure that your current working directory is the
project top-level directory. To do this, enter the following command:
```
cd <project directory name>
```

**Note**: Making your current working directory the project top-level directory will ensure
that the option to add models and data sources is available when you open the API Designer. If you
open the API Designer without changing the directory, you will not be able to add models and data
sources.

To open the API Designer, complete the following steps:
1. Open a command line and enter:
```
apic edit
```
    After a brief pause, the following message is displayed.
    ```
    Express server listening on http://127.0.0.1:9000
    ```
    The API Designer opens in your default web browser.

2. In the login page, enter your Bluemix&reg; ID and password. Click **Sign In**.

3. Click **Models**.

4. Click **Add**. The LoopBack&reg; **Model** window opens.

5. Enter a model name.
In general, you can use any alphanumeric characters plus dashes and underscores in a model
name.

6. Click **New**.

7. In the model editor page, go to Properties and click **Add**.

8. Enter the Property Name and select a Type

9. When you finish entering the Properties for the model, click **Save**.

By default, an empty LoopBack&reg; project does not have any data sources defined. To define a data source, complete the following steps:
1. Click **Data Sources**.

2. Click the **Add** icon.
The New LoopBack&reg; **Model** window opens.

3. Enter a data source name. You can use any alphanumeric character, dashes, and underscores in a data source
name.

4. Click **New**.
The data source appears in the list of data sources, and the editor updates the
`server/datasources.json` file with settings for the new data source.

5. Click your data source to view its settings.

6. Change the Connector setting to the connector that you require.

7. Go back to the console where you started the API Designer and install the Connector by entering
the following command:
```
npm install --save <connector-package>
```
    where `<connector-package>` is the name of the npm package for the LoopBack&reg; connector you selected. See the following table for a list of connector packages.

**Note:** The in-memory and email connectors are built in to LoopBack&reg;, so you do not need to install them.

<table>
<caption>Table 3. LoopBack Connectors</caption>
<thead>
<tr class="style-scope doc-content doc-tr-even">
<th style="width: 50%" id="d70e1489" class="thleft style-scope doc-content">Data source</th>
<th style="width: 50%" id="d70e1491" class="thleft style-scope doc-content">Connector Package</th>
</tr>
</thead>
<tbody>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Cloudant</td>
<td style="width: 50%">loopback-connector-cloudant</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DashDB</td>
<td style="width: 50%">loopback-connector-dashdb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">DB2</td>
<td style="width: 50%">loopback-connector-db2</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">DB2 for zOS</td>
<td style="width: 50%">loopback-connector-db2z</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">Microsoft SQL Server</td>
<td style="width: 50%">loopback-connector-mssql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">MongoDB</td>
<td style="width: 50%">loopback-connector-mongodb</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">MySQL</td>
<td style="width: 50%">loopback-connector-mysql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">Oracle</td>
<td style="width: 50%">loopback-connector-oracle</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">PostgreSQL</td>
<td style="width: 50%">loopback-connector-postgresql</td>
</tr>
<tr class="style-scope doc-content doc-tr-even"><td style="width: 50%" headers="d70e1489 ">SOAP web services</td>
<td style="width: 50%">loopback-connector-soap</td>
</tr>
<tr class="style-scope doc-content doc-tr-odd"><td style="width: 50%" headers="d70e1489 ">REST web services</td>
<td style="width: 50%">loopback-connector-rest</td>
</tr>
</tbody>
</table>

For more information, see [LoopBack Documentation - Building a connector](https://http://loopback.io//doc/en/lb3/Defining-data-sources.html).

**Note:** If you selected the Oracle connector, you must set an environment variable in
{{site.data.keyword.Bluemix_short}} for the Oracle app to start. To
do this, complete the following steps:

1. In the {{site.data.keyword.Bluemix_short}} UI, select
**Compute**.

2. In CF Applications, select the application that you want to work with.

3. Click **Runtime**.

4. Select **Environment Variables**.

5. In the User-Defined section, click **ADD**.

6. In the **Name** field, enter `LD_LIBRARY_PATH`.

7. In the **Value** field, enter
`$LD_LIBRARY_PATH:/home/vcap/app/node_modules/instantclient`.

8. Click **Save**.

To test a LoopBack&reg; project, complete the following steps:
1. Click the **Start the servers** icon.
The following message is displayed:
```
http://localhost:<4001/>Running
```
Depending on your
project configuration and whether other processes are running, a different port number may be
displayed.

2. Click **localhost:4001** to display the API root endpoint. For the default
LoopBack&reg; (empty or hello-world) project, you see
something like this:
```
{"started":"2017-03-07T22:24:55.322Z","uptime":35.839}
```

Next, you need to create a Product. For more information, see [Creating Products](managing_products.html#create_products).
**Tip**: Whenever you start a new command prompt, make sure that your current working
directory is the project top-level directory. To do this, enter the following
command:
```
cd <project directory name>
```

## Uninstalling the developer toolkit
{: #uninstall_dev_tk}

### Prerequisites

Before you begin, you must stop any apps that are running locally by entering the following
command:
```
apic stop --all
```

To uninstall the developer toolkit, complete the following steps:
1. Enter the following command:
```
npm rm -g apiconnect
```
{: codeblock}

2. Clear your npm cache:
```
npm cache clean
```

If you are using Windows:

3. Delete all files whose names begin with `npm-` in `C:\Users\username\AppData\Local\Temp`
4. Delete the directory `<home_dir>\.apiconnect`, where `<home_dir>` is the home directory of the user account under which the toolkit was previously installed.
