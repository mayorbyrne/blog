---
title: Tailwind intellisense in neovim
date: 2024-09-27 20:26:08
tags:
---

### How I got Tailwind intellisense working in neovim

I recently started using Tailwind CSS in a project and wanted to get intellisense working in neovim. Fortunately, the tailwindcss language server is available through the `Mason` neovim plugin.

![](/images/mason.png)

After the language server was installed and set up in my neovim init, I opened an html file I was writing tailwind inside of using the tailwind CDN, but I wasn't getting any intellisense. In the screenshot below, the only intellisense I got when typing `text` was a `textarea` snippet. This was a little confusing, as I clearly had the language server installed properly.

![](/images/nosense.png)

I decided to run `:LspInfo` to see if the language server was running properly, and I saw that it was available, but not attached to the current buffer and running.

![](/images/lspinfo.png)

I started thinking that perhaps the language server wasn't being triggered on a plain html file. I decided to add a blank tailwind config file (`tailwind.config.js`) to the root directory where the html lived.

![](/images/config.png)

I restarted neovim, re-opened the html file, typed `:LspInfo`, and saw some more promising results. The tailwind language server was now connected to the html file buffer!

![](/images/lspinfo2.png)

Once again I started typing `text`, and this time I got the intellisense I was looking for!

![](/images/intellisense.png)

### Conclusion
Make sure your language server is installed properly, and make sure you have a tailwind config file in the root directory of the file you're working in. This should get you up and running with Tailwind intellisense in neovim.
```
