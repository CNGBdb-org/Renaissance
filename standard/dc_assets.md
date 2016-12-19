# sub-directory in `dc_assets`
`dc_assets` has five types of directory:
- `admin` is the resource directory for django admin site.
- `dc_cache` is the cache directory for all projects. its sub-directory must be named with format: `dc_[project_code_name]`, e.g. `dc_1kite`.
- `dc_public` is the public directory for public resource. it contains sub-directories: `js`, `css`, `plugins`, `img`, `data`.
- `script` is the directory contains the programs/scripts for minifing the static resource.
- `dc_[project_code_name]` are project-special resource directories. it contains sub-directories: `js`, `css`, `img`, `data`.

## sub-directory in `dc_assets/dc_cache`
sub-directory under this directory must be named with format: `dc_[project_code_name]`, e.g. `dc_1kite`. lower case only.
this is be set in `settings.py` file:
```
# no need to change COMPRESS_ROOT
COMPRESS_ROOT = '/dc_assets/dc_cache/'
# update COMPRESS_OUTPUT_DIR according to the project
COMPRESS_OUTPUT_DIR = 'dc_1kite'
```

## sub-directory in `dc_assets/dc_public`
this directory contains five sub-directories: 
- `js` is the directory contains all the custom but public javascript libary files.
- `css` is the directory contains all the custom but public javascript libary files.
- `plugins` is the directory stores the 3rd-party plugins.
- `img` is the directory stores all the custom but public images, including all logos.
- `font` is the directory stores all the local fonts.
- `data` is the directory stores all the custom but public data file, e.g. csv files, json files, etc.

### `dc_assets/dc_public/js`
only two roles for this directory: 
- name of files/directores must be clearly telling what functions it is doing for. lower case only.
- two versions of every file, one is readable, the other one is minified. assuming we has a file called `auth.js`, we can tell from the file name that it is used for authentication, and there must be a minified version `auth.min.js`.

### `dc_assets/dc_public/css`
only two roles for this directory: 
- name of files/directores must be clearly telling what frame it is can be used for. lower case only.
- every file must has two versions, one is readable, the other one is minified. assuming we has a file called `bordered_form.css`, we can tell from the file name that it is can be used to styling bordered forms, and there must be a minified version `bordered_form.min.css`.

### `dc_assets/dc_public/plugins`
two roles for this directory are a little complicate. 
- `[plugin directory]` is the only type of sub-directory under `plugins`, and must be named with the plugin name only, no version number, and must use lower case letters and underscore only. e.g. `bootstrap`.
- `[version directory]` is the only type of sub-directory under `[plugin directory]`, and must be named with the version number(lower case only) only and do not name it starting with `v`, e.g. `bootstrap/3.3.7`. if you cannot find out the version number of the plugin, use the date when you download it as version number, e.g. `bootstrap/20160912`.
- files are not allowed be put into `plugins` directly. 

### `dc_assets/dc_public/img`
- files are not allowed be put into `img` directly.
- `[type directory]` is the sub-directory under `img` and its name must be clearly telling what type of images it is. lower case only.
- `[class directory]` is the sub-directory under `[type directory]` and its name must be clearly telling what class of images it is. lower case only. this sub-directory is not necessary, only if the images of `[type directory]` can be sorted into class. `[class directory]` can only contains files.
- every file must has two versions, one is raw, the other one is minified. assuming we has a file called `logo/standard/1kite.png`, we can tell from the names of path and file that it is a standard(full-color) logo, and there must be a minified version `logo/standard/1kite.min.png`. letters must be lower case.

### `dc_assets/dc_public/font`
- `[font directory]` is the only type of sub-directory under `plugins`, and must be named with the font name only, no version number, and must use lower case letters and underscore only. e.g. `open_sans`.
- `[version directory]` is the only type of sub-directory under `[font directory]`, and must be named with the version number(lower case only) only and do not name it starting with `v`, e.g. `open_sans/13`. if you cannot find out the version number of the plugin, use the date when you download it as version number, e.g. `open_sans/20160912`.
- `[type name].suffix` is the format for font files under `[version directory]`, lower case letters and underscore only, e.g. `light.woff`, `light_italic.woff`.
- `font.css` is the font family defining for related font and must be under `[version directory]`, all the font path must be absolute path.
- files are not allowed be put into `font` and `[font directory]` directly. 

### `dc_assets/dc_public/data`
detail to follow.

## sub-directory in `dc_assets/script`
roles for this directory:
- all the files/directories of this directory can not be servered as static resource.
- all the files must be named with format `[program name][_/-][version number].suffix`. the connectting character can be underscore or minus. letters must be lower case.
- all the directories must be named with format `[program name]/[version number]`. the slash in the format means sub-directory. roles follow the ones of `dc_assets/dc_public/plugins`.

## sub-directory in `dc_assets/dc_[project code name]`
this directory contains four sub-directories: 
- `js` is the directory contains all the page-special javascript libary files.
- `css` is the directory contains all the page-special javascript libary files.
- `img` is the directory stores all the page-special images, put logos in `dc_assets/dc_public/img` instead of this one.
- `data` is the directory stores all the page-special data file, e.g. csv files, json files, etc.
all the roles of these four directories follow the ones in `dc_assets/dc_public`
