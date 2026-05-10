## How to Contribute

The [MelbCSS](https://melbcss.com/) site serves as a blank canvas for creativity! We have built the site to allow for users to fork style and submit changes to be reviewed and showcased on our home page!

If you are new to git/github and need help submitting your design you can [join the discord](https://discord.gg/QQS82ZQfDt) to get further information!

### Forking and Local Setup

To start working on your custom theme

1. **Fork the Repository**: Click the Fork button at the top-right of the repository to create a copy under your GitHub account.
2. **Clone Locally**:

```Bash
git clone https://github.com/<your_username_>/website
cd website
```

3. Create a Branch: Always work on a new branch rather than main. Use a name to help you track your contribution.

```Bash
git -switch -c your-branch-name
```

4. Start working on your CSS!

### Setting up your CSS file

To ensure your theme is recognized and easy to manage, please follow these steps:

1. Create your file: In the styles/ directory, create a new CSS file.
2. Naming Convention: Use the format `<themename>-<yourname>.css`.
    - Example: `synthwave-asbedb.css`
3. Use Variables - currently the site supports dark and light mode using variables, if you would like a toggle to be functional you can make use of some native css!
4. Register your theme: Open `index.html` and locate the `<select id="style-select">` tag. Add a new `<option>` with your filename as the value:

```html
<select id="style-select" autocomplete="off">
    <option value="default.css">Default</option>
    <!-- Add yours below -->
    <option value="synthwave-asbedb.css">Synthwave by AsbedB</option>
</select>
```

### Checklist

Before submitting your Pull Request, please ensure:

- [ ] My file follows the naming convention: themename-username.css.
- [ ] I have added my theme as an `<option>` in the index.html select box.
- [ ] I have tested select and other toggles with my theme active.
- [ ] I have removed any unnecessary "test" code or debug borders.

### Submitting a Pull Request (PR)

Once you have implemented your changes and verified they work locally follow these steps to submit your contribution:

1. Push Your Changes

```Bash
git add .
git commit -m "Add theme: <Your Theme Name>"
git push origin your-branch-name
```

2. Open the PR
    - Navigate to the original website repository on GitHub. You should see a prompt to "Compare & pull request."
3. PR Requirements
    - Include the checklist in your PR comment
4. Review Process
    - Once submitted, the maintainers will review your code.
    - Feedback: You might be asked to make small adjustments. Simply commit the changes to the same branch and push them; the PR will update automatically.
    - Approval: Once approved, your code will be merged and visible on [the website](https://melbcss.com/)
