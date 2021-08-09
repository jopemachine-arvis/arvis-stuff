# The reason that I started to make Arvis

* Lots of alfred-workflows works in `cross-platform`. I always felt like I wanted to use Alfred's workflow when I used another OS.

* I thought the format alfred-workflow uses is easy enough to convert.

* I just wanted to try to create something useful as a graduation work.

* I would like to fix some things that I've thought it is great to fix some problems while I'm writing some alfred workflows.

Below is the list that I thought.

---

1. **It could be a little difficult to find useful alfred workflows.**

* Lots of workflows just exist github without enough promotion.

* There is workflow collection site called `packal`, but `packal` is zombie, haven't been maintained for a long time.

* `packal` isn't familiar with many people, not all workflows are uploaded in the `packal`.

* I thought implementing store feature could be possible in new platform.

2. **I thought it is great to have `quicklook` renderer in making `alfred-evernote-workflow`.**

* In `alfred-evernote-workflow`, workflow cache user's notes in form of `html`, and renders in quicklook window of mac because html is unique option that I have to render the contents of note.

* I've thought it is very helpful to have more powerful renderer supporting `html`, `pdf`, `markdown`, `normal text`.

* I thought if I choose `electron` loading full feature of `chromium`, it is very easy and affordable to support these renderers in cross-platform.

* quicklook window is separate window, so while I'm looking the content of quicklook window, I cannot look the contents of alfred. I didn't like that I cannot look `quicklook` and `alfred window` at the same time.

3. **About nested scriptfilters**

* When scriptfilter overlaps more than 2, pressing `esc` key make alfred hide.

* I wanted to user can return the previous scriptfilter when scriptfilter is nested.

* So, I implemented trigger state as stack.

4. **More freer extension support.**

* In Alfred, when I use some extension, I must type some command.

* In some kind of extension, this process might means just waste of time.

* For example, when I would like to find some file through extension, I cannot find the file through only typing file name. I must type some command to execute the command. Finding file through just file name is not attainable through `workflow`, so alfred provides some builtin feature like file searching, calculating and other necessory utilitys. but I wanted try to make this process other kind of extension.

