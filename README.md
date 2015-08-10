# Go Scratch Mode

This is a little package for experimenting with Go code without having
to use the Go Playground. Usage is simple: just write the code you
want to play around with, `C-c C-c`, and then the program's stdout
will be printed to the message area. Processes have 3 seconds (by
default) to finish.

### Caveats

- Unlike the Go playground, there's no sandboxing, so you can destroy
  your system if you try hard enough.
- `godoc` and `godef` functions don't work (since they want you to be
  visiting a file).
- Your `go-mode` hooks will run, and some minor modes don't like
  running without a file. `company-go` is an example; if you're
  running into problems, you might try something like the following:

```lisp
(defun my-go-hook ()
  (when buffer-file-name
    (setq-local company-backends '(company-go))))

(add-hook 'go-mode-hook #'my-go-hook)
```
