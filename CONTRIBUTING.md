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
2. Naming Convention: Use the format `<themename>.css`.
    - Example: `synthwave.css`
3. Add a CSS comment as the first line with the theme name and author.
    - Example: `/* Theme: Synthwave | Author: AsbedB */`
4. Use Variables - currently the site supports dark and light mode using variables, if you would like a toggle to be functional you can make use of some native css!
    - The dark/light toggle is a checkbox that flips `color-scheme`, with no JavaScript, so any colour written with `light-dark()` follows it.
    - For anything else that changes in dark mode, such as a background image, the toggle flips the system's choice, so dark mode is either of these (Mario's clouds are an example):

```css
@media (prefers-color-scheme: dark) {
    html:not(:has(#mode-toggle-checkbox:checked)) { /* dark */ }
}
@media (prefers-color-scheme: light) {
    html:has(#mode-toggle-checkbox:checked) { /* dark */ }
}
```
5. Register your theme: create `_themes/<themename>.md`, named like your CSS file, with your theme's name and yours:

```markdown
---
title: Synthwave
author: AsbedB
---
```

That is all it takes: your theme joins the theme picker, and gets a page of its own at `/<themename>/` (for example `https://melbcss.com/synthwave/`), which works even with JavaScript turned off.

### Previewing your theme

GitHub Pages builds the site with [Jekyll](https://jekyllrb.com/), which turns `_layouts/home.html` into the home page and one page per theme. To build and serve it locally the same way, with [Docker](https://www.docker.com/) running, from the repository's folder:

```Bash
docker run --rm -p 4000:4000 -v "$PWD:/site" -e RUBYOPT=-rgithub-pages \
    --entrypoint bundle ghcr.io/actions/jekyll-build-pages:v1.0.13 \
    exec jekyll serve -s /site -d /tmp/site -H 0.0.0.0 --watch --force_polling
```

Then open http://localhost:4000/<themename>/. The site rebuilds when you save a file; reload the page to see the change.

### Checklist

Before submitting your Pull Request, please ensure:

- [ ] My file follows the naming convention: themename.css.
- [ ] My CSS file starts with a comment containing the theme name and author.
- [ ] I have added `_themes/<themename>.md` with my theme's title and author.
- [ ] I have tested the theme menu and other toggles with my theme active. The menu's button is a `.link-button`, and its list is `.theme-menu-content`.
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
