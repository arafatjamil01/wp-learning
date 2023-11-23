# How to activate PHPStorm SCSS configuration for rendering

Install sass using npm globally - `npm install -g sass`
Go to file watcher in phpstorm and write the following arguments and path in the right field and hit apply.
Arguments:`$FileName$:$FileParentDir$/css/$FileNameWithoutExtension$.css`  

Output paths to
refresh: `$FileParentDir$/css/$FileNameWithoutExtension$.css:$FileParentDir$/css/$FileNameWithoutExtension$.css.map`

This should do the trick, if you change the folder structure, the structure of arguments as well as output paths to
refresh will be changed.