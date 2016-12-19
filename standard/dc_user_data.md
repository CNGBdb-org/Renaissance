# sub-directory in `dc_user_data`
roles for sub-directories:
- `dc_blast` is the directory for results of all the BLAST jobs of all the projects, BLAST results can not be stored in other directory.
- `dc_[project code name]` is the project-special directory .
- `dc_blast` and `dc_[project code name]` must contains a sub-directory `result`.

## `dc_[project code name]`
an external sub-directory in `dc_[project code name]` is `data`:
sub-directories of `data` is user-special and named with the user id(a MD5 value).

## roles for sub-directories of `results`
- `YYYY-MM-DD` is the format for sub-directories of `results`, it is the date when the job created.
- `[job id]` is the format for sub-directories of `YYYY-MM-DD`, it is the id of job, and the id is project-special.
