
> `gptel-watch` Inspired by `aider --watch-files`

# gptel-watch

`gptel-watch` is an Emacs minor mode that automatically invokes `gptel-request` when the user types certain lines that indicate intent — for example, lines ending with `"AI!"` or `"#ai"`. It uses GPT-style large language models to assist writing or coding directly within your buffer, based on local context.

This package builds on [`gptel`](https://github.com/karthink/gptel), providing a lightweight, pattern-driven workflow for triggering GPT responses while typing.

---

## Preview
![preview](preview.gif)

---

## Installation

```elisp
(use-package gptel-watch
  :after gptel
  :load-path "/path/gptel-watch/"
  :config
  (gptel-watch-global-mode 1))  ;; Optional: enable globally
```

## Usage
Once enabled, write a line like this:
```C
// Print Hello World. AI!
```
Then press `RET`. The line will be replaced with the GPT-generated result, such as:
```C
printf("Hello World");
```

## How to Context extraction
1. `Current Defun`: Current definition under cursor
2. `Relative Line`: Up/Down a line
3. `Range Line`: Precise line number range of the current buffer
4. `Only Current Line`: Only the current line, do not extract context.
5. `And more` ........

## Customization

| Variable                       | Description                                                                                              |
|--------------------------------|----------------------------------------------------------------------------------------------------------|
| `gptel-watch-trigger-patterns` | List of regex patterns. If a line ends with any of these, it triggers GPT. Default: `("AI" "AI!" "#ai")` |
| `gptel-watch-trigger-commands` | List of Emacs commands that can trigger checking. Default: `(newline org-return)`                        |
| `gptel-watch-system-prompt`    | The system prompt sent to GPT along with the context. Guides the style and constraints of the reply.     |


