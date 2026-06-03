# hugo papermod theme customization

This is a fork of the hugo PaperMod theme from [adityatelange/hugo-PaperMod](https://github.com/adityatelange/hugo-PaperMod). Changes made:

1. Disabled smooth scrolling animation in `layouts/_partials/footer.html` by changing `scrollIntoView` behavior to "auto":
    ```js
    document.querySelector(`[id='${decodeURIComponent(id)}']`).scrollIntoView({
                    behavior: "auto"
                });
    ```

2. Added
    ```css
    font-family: "Menlo", "Monaco", "Consolas", "Courier", monospace;
    ``` 
    in `.post-content code` and `.post-content pre code` blocks in `assets/css/common/md-content.css` to make the code font smoother.

3. Changed code highlighting theme to monokai. First, generate style sheet with
    ```shell
    cd themes/papermod/assets/css/includes
    hugo gen chromastyles --style=monokai > chroma-styles.css
    ```
    then set the following keyword color in `chroma-styles.css`:
    ```css
    /* Keyword */ .chroma .k { color: #f92672 }
    ```

4. Adjusted light theme color values in `assets/css/core/theme-vars.css`.

5. Installed the [hugo-cite](https://github.com/3ffe/hugo-cite) theme for managing bibliographies. Added
    ```html
    <link rel="stylesheet" type="text/css" href="{{ "/hugo-cite.css" | relURL }}" />
    ```
    in `themes/papermod/layouts/_partials/extend_head.html`.

6. Enable LaTeX Math rendering. Added `layouts/_partials/math.html`. Added code block
    ```go
    {{ if or .Params.math .Site.Params.math }}
    {{ partial "math.html" . }}
    {{ end }}
    ```
    in `layouts/_partials/extend_head.html`.