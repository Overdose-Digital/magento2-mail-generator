# magento2-mail-generator
Generate HTML and LESS code for mails. Magento2-mail-generator this is a fork [foundation-emails-template](https://github.com/zurb/foundation-emails-template)

## Document navigation
0. [About](#About)
1. [Installation](#Installation)
2. [Build Commands](#Build-Commands)
3. [HTML Structure](#HTML-Structure)
4. [Less Structure](#Less-Structure)
5. [Odinky](#Odinky)
6. [Odinky components](#Odinky-components)
    1. [Grid](#Grid)
    2. [Table-content](#Table-content)
    3. [Banner](#Banner)
    4. [Buttons](#Buttons)
    5. [Spacer](#Spacer)
    6. [Alignment](#Alignment)
    7. [Horizontal rule](#Horizontal-rule)

7. [Litmus Tests](#Litmus-Tests)
8. [Manual email tests](#Manual-email-tests)
9. [List of supported HTML attributes](#List-of-supported-HTML-attributes)
10. [Changelog](#Changelog)

## About

It has a Gulp-powered build system with these features:

- Handlebars HTML templates with [Panini](http://github.com/zurb/panini)
- Simplified HTML email syntax with ODInky - this is a fork [Inky](http://github.com/zurb/inky)
- LESS compilation
- Image compression
- Built-in BrowserSync server
- Full email inlining process

## Installation
1. clone project files
`git clone git@github.com:Overdose-Digital/magento2-mail-generator.git`

2. open project dir

3. install packages.
`npm install`

4. from `od-libs` folder: clone libraries to --> `node_modules`

5. will start the project.
`npm start`

- - -

## Build Commands

Run `npm start` to kick off the build process. A new browser tab will open with a server pointing to your project files.

Run `npm run build` to inline your CSS into your HTML along with the rest of the build process.

Run `npm run litmus` to build as above, then submit to litmus for testing. *AWS S3 Account details required (config.json)*

Run `npm run mail` to build as above, then send to specified email address for testing. *SMTP server details required (config.json)*

Run `npm run zip` to build as above, then zip HTML and images for easy deployment to email marketing services. 

- - -

## HTML Structure
Magento2-mail-generator follows a simple and easy to customize coding structure. Here is the sample for your reference:

- `src/assets/` - Contains all of the assets referenced
- `src/assets/components/` - components that you can connect to templates
- `src/assets/templates/` - templates Files
- `src/assets/templates/index.html` - ODemail Homepage
- `src/assets/templates/youNewTemplate.html` - created new template hire
- `src/assets/web/` - Contains all of the assets referenced
- `src/assets/web/images/` - Images files
- `src/assets/web/css/` - LESS files

- - -

## Less Structure
We have added LESS `.less` files in template. You can find less file here - `src/assets/web/css`
Open the `src/assets/web/css/_variables.scss` and edit the values according to your needs. If you need more Advanced Setup then you can edit the Respective Files yourself which have been branched inside the same Folder. It is completely at your discretion only to include the Required `.less`
Files you need to minimize the amount of CSS & including only the Styles of the Blocks you need. This can be setup in your `email-inline.less` File.

- - -

## Odinky
OdInky is a templating language that converts simple HTML tags into the complex table HTML required for emails.

> Odinky - his fork inky lib

Grid:
- `<container>`
- `<table-content>`
- `<row>`
- `<columns>`
Button: 
-`<button>`, `<button-secondary>`, `<button-link>`
Spacer: 
- `<spacer>`
Menu:
-`<menu>`
-`<item>`
Banner: 
-`<banner>`

*You can set custom styles for any component:*
<pre><code>
  &lt;container class=&quot;custom-style&quot;&gt;
    &lt;row class=&quot;custom-style&quot;&gt;
      &lt;columns col=&quot;12&quot; class=&quot;custom-style&quot;&gt;
         &lt;p&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque pretium id diam nec ornare. Interdum et malesuada fames ac ante ipsum primis in faucibus. Maecenas vitae condimentum velit. Praesent rhoncus, nisl et vestibulum tincidunt, turpis sem tincidunt mi, nec dictum urna nisi ullamcorper ante. Maecenas eu turpis id urna rhoncus ultrices. Nam maximus sollicitudin pharetra. Donec velit quam, vulputate ut malesuada at, laoreet et magna. Sed vitae risus sed libero posuere feugiat vel vehicula augue. &lt;/p&gt;
       &lt;button class=&quot;custom-style&quot; href=&quot;#link&quot;&gt;btn name&lt;/button&gt;
      &lt;/columns&gt;
    &lt;/row&gt;
  &lt;/container&gt;
</code></pre>
### HTML:
<pre><code>
  &lt;table align=&quot;center&quot; class=&quot;container custom-style&quot;&gt;
    &lt;tbody&gt;
      &lt;tr&gt;
        &lt;td&gt;
          &lt;h2 class=&quot;text-center&quot;&gt;Custom style for component&lt;/h2&gt;
          &lt;table class=&quot;row custom-style&quot;&gt;
            &lt;tbody&gt;
              &lt;tr&gt;
                &lt;th class=&quot;custom-style col-12 columns&quot;&gt;
                  &lt;table&gt;
                    &lt;tbody&gt;
                      &lt;tr&gt;
                        &lt;th&gt;
                          &lt;p&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque pretium id
                            diam nec ornare. Interdum et malesuada fames ac ante ipsum primis in
                            faucibus. Maecenas vitae condimentum velit. Praesent rhoncus, nisl et
                            vestibulum tincidunt, turpis sem tincidunt mi, nec dictum urna nisi
                            ullamcorper ante. Maecenas eu turpis id urna rhoncus ultrices. Nam maximus
                            sollicitudin pharetra. Donec velit quam, vulputate ut malesuada at, laoreet
                            et magna. Sed vitae risus sed libero posuere feugiat vel vehicula augue.
                          &lt;/p&gt;
                          &lt;table class=&quot;button custom-style&quot;&gt;
                            &lt;tbody&gt;
                              &lt;tr&gt;
                                &lt;td&gt;
                                  &lt;table&gt;
                                    &lt;tbody&gt;
                                      &lt;tr&gt;
                                        &lt;td&gt;&lt;a href=&quot;#link&quot;&gt;btn name&lt;/a&gt;&lt;/td&gt;
                                      &lt;/tr&gt;
                                    &lt;/tbody&gt;
                                  &lt;/table&gt;
                                &lt;/td&gt;
                              &lt;/tr&gt;
                            &lt;/tbody&gt;
                          &lt;/table&gt;
                        &lt;/th&gt;
                        &lt;th class=&quot;expander&quot;&gt;&lt;/th&gt;
                      &lt;/tr&gt;
                    &lt;/tbody&gt;
                  &lt;/table&gt;
                &lt;/th&gt;
              &lt;/tr&gt;
            &lt;/tbody&gt;
          &lt;/table&gt;
        &lt;/td&gt;
      &lt;/tr&gt;
    &lt;/tbody&gt;
  &lt;/table&gt;
</code></pre>

- - -

## Odinky components
- - -

### Grid
The grid has two core elements: the row and column. Rows define horizontal sections of content, and columns carve up the row into side-by-side sections.
A column has a size between 1 and *12—this* is how many columns wide the element is. ODemail uses a 12-column grid, so 6 columns is half the width of the whole row.

**ODinky**
<pre><code>
&lt;row&gt;
    &lt;columns col=&quot;4&quot;&gt;
    &lt;center&gt;
        &lt;img src=&quot;https://placehold.co/100x150/777777/&amp;text=images&quot; alt=&quot;&quot; class=&quot;demo-col__img&quot;&gt;
    &lt;/center&gt;
    &lt;/columns&gt;
    &lt;columns col=&quot;8&quot;&gt;
    &lt;p&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque pretium id diam nec ornare. Interdum et malesuada fames ac ante ipsum primis in faucibus. Maecenas vitae condimentum velit. Praesent rhoncus, nisl et vestibulum tincidunt, turpis sem tincidunt mi, nec dictum urna nisi ullamcorper ante. Maecenas eu turpis id urna rhoncus ultrices. Nam maximus sollicitudin pharetra. Donec velit quam, vulputate ut malesuada at, laoreet et magna. Sed vitae risus sed libero posuere feugiat vel vehicula augue. &lt;/p&gt;
    &lt;/columns&gt;
&lt;/row&gt;
</code></pre>
            
**html**
<pre><code>
&lt;table class=&quot;row&quot;&gt;
    &lt;tbody&gt;
    &lt;tr&gt;
        &lt;th class=&quot;col-4 columns&quot;&gt;
        &lt;table&gt;
            &lt;tbody&gt;
            &lt;tr&gt;
                &lt;th&gt;
                &lt;center&gt;
                    &lt;img src=&quot;https://placehold.co/100x150/777777/&amp;text=images&quot; alt
                    class=&quot;demo-col__img float-center&quot; align=&quot;center&quot;&gt;
                &lt;/center&gt;
                &lt;/th&gt;
            &lt;/tr&gt;
            &lt;/tbody&gt;
        &lt;/table&gt;
        &lt;/th&gt;
        &lt;th class=&quot;col-8 columns&quot;&gt;
        &lt;table&gt;
            &lt;tbody&gt;
            &lt;tr&gt;
                &lt;th&gt;
                &lt;p&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit. Quisque pretium id diam
                    nec ornare. Interdum et malesuada fames ac ante ipsum primis in faucibus. Maecenas
                    vitae condimentum velit. Praesent rhoncus, nisl et vestibulum tincidunt, turpis sem
                    tincidunt mi, nec dictum urna nisi ullamcorper ante. Maecenas eu turpis id urna
                    rhoncus ultrices. Nam maximus sollicitudin pharetra. Donec velit quam, vulputate ut
                    malesuada at, laoreet et magna. Sed vitae risus sed libero posuere feugiat vel
                    vehicula augue. &lt;/p&gt;
                &lt;/th&gt;
            &lt;/tr&gt;
            &lt;/tbody&gt;
        &lt;/table&gt;
        &lt;/th&gt;
    &lt;/tr&gt;
    &lt;/tbody&gt;
&lt;/table&gt;
</code></pre>
  

- - -


### Table-content
When using Inky HTML, the `&lt;table-content&gt;` tag will create a `&lt;table&gt;`, `&lt;tr&gt;`, `&lt;th&gt;` structure needed to create consistent full width backgrounds. You can add classes to the wrapper to target CSS properties on it or target elements within it. The .table-content__inner class is available to add padding to the wrapper.

**ODinky**
<pre><code>
&lt;table-content&gt;
    &lt;h1&gt;OD test email&lt;/h1&gt;
    &lt;p class=&quot;table-content__text&quot;&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit. In dapibus metus at bibendum maximus.&lt;a href=&quot;https://site.com&quot; class=&quot;table-content__link&quot;&gt;youLink&lt;/p&gt;
&lt;/table-content&gt;
</code></pre>
            
**html**
<pre><code>
&lt;table align=&quot;center&quot; class=&quot;table-content&quot;&gt;
    &lt;tbody&gt;
    &lt;tr&gt;
        &lt;td class=&quot;table-content__inner&quot;&gt;
        &lt;h1&gt;OD test email&lt;/h1&gt;
        &lt;p class=&quot;table-content__text&quot;&gt;Lorem ipsum dolor sit amet, consectetur adipiscing elit. In dapibus metus at bibendum maximus. &lt;a href=&quot;https://site.com&quot; class=&quot;table-content__link&quot;&gt;youLink&lt;/p&gt;
        &lt;/td&gt;
    &lt;/tr&gt;
    &lt;/tbody&gt;
&lt;/table&gt;
</code></pre>

  
- - -


### Banner
  
**ODinky**
<pre><code>
&lt;banner&gt;
    &lt;img src=&quot;web/images/email/demo/banner.png&quot; class=&quot;banner__img&quot;&gt;
&lt;/banner&gt;     
</code></pre>
            
**html**
<pre><code>
&lt;table align=&quot;center&quot; class=&quot;banner&quot;&gt;
    &lt;tbody&gt;
    &lt;tr&gt;
        &lt;td class=&quot;banner__inner&quot;&gt;
        &lt;center&gt;
            &lt;img src=&quot;web/images/email/demo/banner.png&quot; class=&quot;banner__img&quot; align=&quot;center&quot;&gt;
        &lt;/center&gt;
        &lt;/td&gt;
    &lt;/tr&gt;
    &lt;/tbody&gt;
&lt;/table&gt;            
</code></pre>
  
 
- - -

 
### Buttons
Buttons are convenient tools when you need more traditional actions. To that end, *OdEmail* has many easy to use button styles that you can customize or override to fit your needs.
Creating a bullet-proof button that works in all email clients requires a table nested inside of a table. Put the class `.button` on the outer `&lt;table&gt;`. Inside of the inner table, put an `&lt;a&gt;` with an `href` attribute containing your link.
In Inky HTML, the `&lt;button&gt;` tag creates all of this markup for you.
**ODinky**
<pre><code>
    &lt;button href=&quot;#&quot;&gt;Button&lt;/button&gt;
    &lt;button-secondary href=&quot;#&quot;&gt;Secondary&lt;/button-secondary&gt;
    &lt;button-link href=&quot;#&quot;&gt;Btn link&lt;/button-link&gt;
</code></pre>
                
**html**
<pre><code>
  &lt;table class=&quot;button&quot;&gt;
      &lt;tbody&gt;
      &lt;tr&gt;
          &lt;td&gt;
          &lt;table&gt;
              &lt;tbody&gt;
              &lt;tr&gt;
                  &lt;td&gt;&lt;a align=&quot;center&quot; href=&quot;#&quot;&gt;Button&lt;/a&gt;&lt;/td&gt;
              &lt;/tr&gt;
              &lt;/tbody&gt;
          &lt;/table&gt;
          &lt;/td&gt;
      &lt;/tr&gt;
      &lt;/tbody&gt;
  &lt;/table&gt;
  &lt;table class=&quot;button-secondary&quot;&gt;
      &lt;tbody&gt;
      &lt;tr&gt;
          &lt;td&gt;
          &lt;table&gt;
              &lt;tbody&gt;
              &lt;tr&gt;
                  &lt;td&gt;&lt;a align=&quot;center&quot; href=&quot;#&quot;&gt;Secondary&lt;/a&gt;&lt;/td&gt;
              &lt;/tr&gt;
              &lt;/tbody&gt;
          &lt;/table&gt;
          &lt;/td&gt;
      &lt;/tr&gt;
      &lt;/tbody&gt;
  &lt;/table&gt;
  &lt;table class=&quot;button-link&quot;&gt;
      &lt;tbody&gt;
      &lt;tr&gt;
          &lt;td&gt;
          &lt;table&gt;
              &lt;tbody&gt;
              &lt;tr&gt;
                  &lt;td&gt;&lt;a align=&quot;center&quot; href=&quot;#&quot;&gt;Btn link&lt;/a&gt;&lt;/td&gt;
              &lt;/tr&gt;
              &lt;/tbody&gt;
          &lt;/table&gt;
          &lt;/td&gt;
      &lt;/tr&gt;
      &lt;/tbody&gt;
  &lt;/table&gt;
</code></pre>
  
 
- - -

 
### Spacer

**ODinky**
<pre><code>
&lt;p&gt;Stuff on top&lt;/p&gt;
&lt;spacer size=&quot;100&quot;&gt;&lt;/spacer&gt;
&lt;p&gt;Stuff on bottom&lt;/p&gt;
</code></pre>
            
**html**
<pre><code>
&lt;p&gt;Stuff on top&lt;/p&gt;
    &lt;table class=&quot;spacer&quot;&gt;
    &lt;tbody&gt;
        &lt;tr&gt;
        &lt;td height=&quot;100&quot; style=&quot;font-size:100px;line-height:100px;&quot;&gt;&amp;nbsp;&lt;/td&gt;
        &lt;/tr&gt;
    &lt;/tbody&gt;
    &lt;/table&gt;
&lt;p&gt;Stuff on bottom&lt;/p&gt;
</code></pre>

- - -


### Alignment
Centering, images, text, buttons, and menus in HTML emails made easy.
**ODinky**
<pre><code>
  &lt;style&gt;.alignment-col {border: 1px solid #333;}&lt;/style&gt;
  &lt;h3 class=&quot;text-center&quot;&gt;Text Alignment&lt;/h3&gt;
  &lt;row&gt;
    &lt;columns class=&quot;alignment-col&quot;&gt;
      &lt;p class=&quot;text-left&quot;&gt;Left (default)&lt;/p&gt;
    &lt;/columns&gt;
    &lt;columns class=&quot;alignment-col&quot;&gt;
        &lt;p class=&quot;text-center&quot;&gt;center&lt;/p&gt;
    &lt;/columns&gt;
    &lt;columns class=&quot;alignment-col&quot;&gt;
        &lt;p class=&quot;text-right&quot;&gt;right&lt;/p&gt;
    &lt;/columns&gt;
  &lt;/row&gt;
  &lt;h3 class=&quot;text-center&quot;&gt;Aligning Images&lt;/h3&gt;
  &lt;row&gt;
    &lt;columns&gt;
      &lt;img class=&quot;float-left&quot; src=&quot;https://via.placeholder.com/140x100&quot; alt=&quot;&quot;&gt;
      &lt;img class=&quot;float-center&quot; src=&quot;https://via.placeholder.com/140x100&quot; alt=&quot;&quot;&gt;
      &lt;img class=&quot;float-right&quot; src=&quot;https://via.placeholder.com/140x100&quot; alt=&quot;&quot;&gt;
    &lt;/columns&gt;
  &lt;/row&gt;
</code></pre>
                
**html**
<pre><code>
&lt;style&gt;
    .alignment-col {
    border: 1px solid #333;
    }
&lt;/style&gt;
&lt;h3 class=&quot;text-center&quot;&gt;Text Alignment&lt;/h3&gt;
&lt;table class=&quot;row&quot;&gt;
    &lt;tbody&gt;
    &lt;tr&gt;
        &lt;th class=&quot;alignment-col col-4 columns&quot;&gt;
        &lt;table&gt;
            &lt;tbody&gt;
            &lt;tr&gt;
                &lt;th&gt;
                &lt;p class=&quot;text-left&quot;&gt;Left (default)&lt;/p&gt;
                &lt;/th&gt;
            &lt;/tr&gt;
            &lt;/tbody&gt;
        &lt;/table&gt;
        &lt;/th&gt;
        &lt;th class=&quot;alignment-col col-4 columns&quot;&gt;
        &lt;table&gt;
            &lt;tbody&gt;
            &lt;tr&gt;
                &lt;th&gt;
                &lt;p class=&quot;text-center&quot;&gt;center&lt;/p&gt;
                &lt;/th&gt;
            &lt;/tr&gt;
            &lt;/tbody&gt;
        &lt;/table&gt;
        &lt;/th&gt;
        &lt;th class=&quot;alignment-col col-4 columns&quot;&gt;
        &lt;table&gt;
            &lt;tbody&gt;
            &lt;tr&gt;
                &lt;th&gt;
                &lt;p class=&quot;text-right&quot;&gt;right&lt;/p&gt;
                &lt;/th&gt;
            &lt;/tr&gt;
            &lt;/tbody&gt;
        &lt;/table&gt;
        &lt;/th&gt;
    &lt;/tr&gt;
    &lt;/tbody&gt;
&lt;/table&gt;
&lt;h3 class=&quot;text-center&quot;&gt;Aligning Images&lt;/h3&gt;
&lt;table class=&quot;row&quot;&gt;
    &lt;tbody&gt;
    &lt;tr&gt;
        &lt;th class=&quot;col-12 columns&quot;&gt;
        &lt;table&gt;
            &lt;tbody&gt;
            &lt;tr&gt;
                &lt;th&gt;
                &lt;img class=&quot;float-left&quot; src=&quot;https://via.placeholder.com/140x100&quot; alt&gt;
                &lt;img class=&quot;float-center&quot; src=&quot;https://via.placeholder.com/140x100&quot; alt&gt;
                &lt;img class=&quot;float-right&quot; src=&quot;https://via.placeholder.com/140x100&quot; alt&gt;
                &lt;/th&gt;
                &lt;th class=&quot;expander&quot;&gt;&lt;/th&gt;
            &lt;/tr&gt;
            &lt;/tbody&gt;
        &lt;/table&gt;
        &lt;/th&gt;
    &lt;/tr&gt;
    &lt;/tbody&gt;
&lt;/table&gt;
</code></pre>
  
 
- - -

 
### Horizontal rule

**ODinky**
<pre><code>
    &lt;h-line&gt;&lt;/h-line&gt;
</code></pre>
            
**html**
<pre><code>
&lt;table class=&quot;h-line&quot;&gt;
    &lt;tr&gt;
    &lt;th&gt;&amp;nbsp;&lt;/th&gt;
    &lt;/tr&gt;
&lt;/table&gt;
</code></pre>


- - -



## Litmus Tests

Testing in Litmus requires the images to be hosted publicly. The provided gulp task handles this by automating hosting to an AWS S3 account. Provide your Litmus and AWS S3 account details in the `example.config.json` and then rename to `config.json`. Litmus config, and `aws.url` are required, however if you follow the [aws-sdk suggestions](http://docs.aws.amazon.com/AWSJavaScriptSDK/guide/node-configuring.html) you don't need to supply the AWS credentials into this JSON.

```json
{
  "aws": {
    "region": "us-east-1",
    "accessKeyId": "YOUR_ACCOUNT_KEY",
    "secretAccessKey": "YOUR_ACCOUNT_SECRET",
    "params": {
        "Bucket": "elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
    },
    "url": "https://s3.amazonaws.com/elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
  },
  "litmus": {
    "username": "YOUR_LITMUS@EMAIL.com",
    "password": "YOUR_ACCOUNT_PASSWORD",
    "url": "https://YOUR_ACCOUNT.litmus.com",
    "applications": ["ol2003","ol2007","ol2010","ol2011","ol2013","chromegmailnew","chromeyahoo","appmail9","iphone5s","ipad","android4","androidgmailapp"]
  }
}
```

- - -


## Manual email tests

Similar to the Litmus tests, you can have the emails sent to a specified email address. Just like with the Litmus tests, you will need to provide AWS S3 account details in `config.json`. You will also need to specify to details of an SMTP server. The email address to send to emails to can either by configured in the `package.json` file or added as a parameter like so: `npm run mail -- --to="example.com"`

```json
{
  "aws": {
    "region": "us-east-1",
    "accessKeyId": "YOUR_ACCOUNT_KEY",
    "secretAccessKey": "YOUR_ACCOUNT_SECRET",
    "params": {
        "Bucket": "elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
    },
    "url": "https://s3.amazonaws.com/elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
  },
  "mail": {
    "to": [
      "example@domain.com"
    ],
    "from": "Company name <info@company.com",
    "smtp": {
      "auth": {
        "user": "example@domain.com",
        "pass": "12345678"
      },
      "host": "smtp.domain.com",
      "secureConnection": true,
      "port": 465
    }
  }
}
```

For a full list of Litmus' supported test clients(applications) see their [client list](https://litmus.com/emails/clients.xml).

**Caution:** AWS Service Fees will result, however, are usually very low do to minimal traffic. Use at your own discretion.


- - -

## List of supported HTML attributes

List of supported HTML attributes in an email template

| Tag	 | attributes support
| ------ | ------ |
| a      | 	class, href, id, style, target| 
| b      | 	class, id, style| 
| br     | 	class, id, style| 
| p      | 	align, class, dir, id, style| 
| font   | 	class, color, face, id, size, style| 
| h1-h6  | 	align, class, dir, id, style| 
| head   | 	dir, lang| 
| hr     | 	align, size, width| 
| i	     | class, id, style| 
| img    | 	align, border, class, height, hspace, id, src, style, usemap, vspace, width| 
| label  | 	class, id, style| 
| li     | 	class, dir, id, style, type| 
| ol     | 	class, dir, id, style, type| 
| s	     | class, id, style| 
| small	 | class, id, style| 
| span	 | class, id, style| 
| strike | 	class, id, style| 
| strong | 	class, id, style| 
| table	 | align, bgcolor, border, cellpadding, cellspacing, class, dir, frame, id, rules, style, width| 
| td	 | abbr, align, bgcolor, class, colspan, dir, height, id, lang, rowspan, scope, style, valign, width| 
| th	 | abbr, align, background, bgcolor, class, colspan, dir, height, id, lang, scope, style, valign, width| 
| tr	 | align, bgcolor, class, dir, id, style, valign| 
| u	     | class, id, style| 
| ul	 | class, dir, id, style| 

- - -


## Changelog
See what's new added, changed, fixed, improved or updated in the latest versions.

### v 1.0.0
- release

