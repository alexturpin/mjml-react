# mjml-react

(This is forked from Wix's mjml-react — more info why I forked this can be [found in this comment](https://github.com/wix-incubator/mjml-react/issues/52#issuecomment-881830074).)

`MJML` is a markup language created by [Mailjet](https://www.mailjet.com/). But since we are using React in the rest of our app, we want to use React to create the MJML markup for emails.

Note: this does not bundle `mjml` so you can use whatever version of `mjml` you'd like to convert the outputted mjml-string to HTML.

## How it works

Install the required dependencies first:

```bash
npm install react react-dom mjml mjml-react
```

Then you can write:

```js
import {
  render,
  Mjml,
  MjmlHead,
  MjmlTitle,
  MjmlPreview,
  MjmlBody,
  MjmlSection,
  MjmlColumn,
  MjmlButton,
  MjmlImage,
} from "mjml-react";
import mjml2html from "mjml";

const mjmlString = renderToMjml(
  <Mjml>
    <MjmlHead>
      <MjmlTitle>Last Minute Offer</MjmlTitle>
      <MjmlPreview>Last Minute Offer...</MjmlPreview>
    </MjmlHead>
    <MjmlBody width={500}>
      <MjmlSection fullWidth backgroundColor="#efefef">
        <MjmlColumn>
          <MjmlImage src="https://static.wixstatic.com/media/5cb24728abef45dabebe7edc1d97ddd2.jpg" />
        </MjmlColumn>
      </MjmlSection>
      <MjmlSection>
        <MjmlColumn>
          <MjmlButton padding="20px" backgroundColor="#346DB7">
            I like it!
          </MjmlButton>
        </MjmlColumn>
      </MjmlSection>
    </MjmlBody>
  </Mjml>
);

const htmlString = mjml2html(mjmlString);
```

And as the result you will get a nice looking email HTML (works in mobile too!)

![preview](https://user-images.githubusercontent.com/10008149/41058394-59b8ce9e-69d2-11e8-9eb9-c294f35bae9f.png)
