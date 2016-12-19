# `dc_utils` packages
dc_utils includes four packages:
- `account` contains `settings`, `decorators`, `models` and `middlewares` four modules.
- `common` contains `settings` and `middlewares` two modules.
- `mail` contains `settings` and `email` two modules.
- `session` contains `settings`, `middlewares` and `backends` three modules.
# include the `dcc_utils` packages
```
import sys
# append the path of dc_utils into pagckage path
sys.path.append('/dc_utils')
# now you can import the packages/modules/functions
from mail.email import send_thread_email
```
