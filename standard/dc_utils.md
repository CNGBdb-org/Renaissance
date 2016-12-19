# `dc_utils` packages
dc_utils includes four packages:
- `account` contains `settings`, `decorators`, `models` and `middlewares` four modules.
- `common` contains `settings` and `middlewares` two modules.
- `mail` contains `settings` and `email` two modules.
- `session` contains `settings`, `middlewares` and `backends` three modules.

# include the `dc_utils` packages
```
import sys
# append the path of dc_utils into pagckage path
sys.path.append('/dc_utils')
# now you can import the packages/modules/functions
from mail.email import send_thread_email
```

# package `account`
## method `get_account`
Using this method is not suggested, visit the `request.account` instead.
```
from account import get_account
account = get_account(request)
# the account variable has keys: id, pk, username, type_name, is_active, is_authenticated.
# request.account is the same to this account variable.
```

## decorator `login_required`
```
from account.decorators import login_required
@login_required
def your_view_fun(request):
  pass
```
## model object `AnonymousAccount` and `VirsualAccount`
### `AnonymousAccount`
it is readable only and has attributes: id, pk, username, type_name, is_active, is_authenticated.

### `VirsualAccount`
it is callable, pass key-word pairs to it like this: `tmp = VirsualAccount(key1='aaa', key2='bbb')`, and then you visit the key as an attribute of the result: `tmp.key1`.

## middleware `DCAuthenticationMiddleware`
only use it in the project `settings.py` file: `account.middlewares.DCAuthenticationMiddleware`.
this middleware provides `request` with some attributes:
```
request.account.id # None or str
request.account.pk # None or str
request.account.username # blank str or str
request.account.is_active # False or True
request.account.type_name # None or local or github or windows or linkedin or google-plus or qq or weibo or *-linked(* is tpa type)
request.account.is_authenticated # False or True
```

# package `common`
## middleware `DCCommonMiddleware`
only use it in the project `settings.py` file: `common.middlewares.DCAuthenticationMiddleware`.

this middleware provides `request` with some attributes:
```
request.project_list # a list of all projects, item is dict, keys are short_name, icon_uri, logo_uri, uri, full_name_en, full_name_zh
request.meta # a dict of current app, keys are short_name, icon_uri, logo_uri, uri, description_zh, description_en, full_name_zh, full_name_en, author, keywords
request.current_app # structure and content are the same to request.meta
request.login_url # str
request.policy_uri # str
request.terms_uri # str
request.tech_email # str
request.read_notify_uri # str
request.new_notify_uri # str
request.cngb # dict, keys are icon_uri, logo_uri, uri, full_name_zh, full_name_en
request.dc # structure is the same to request.cngb
request.main_nav_template # main navbar template path, only available when settings.MAIN_NAVBAR_FRAME exists
```

# package `mail`
## method `send_thread_email`
```
from mail.email import send_thread_email
from_mail = 'you@example.com'
to_mail_list = ['receiver@example.com',]
subject = 'the title'
content = 'the content'
cc_list = ['cc_receiver@example.com',] # this is optional
bcc_list = ['bcc_receiver@example.com',] # this is optional
html_content = 'html full text content' # this is optional
attacment_list = ['/absolute/path/to/a/file',] # this is optional
send_thread_email(from_email, to_email_list, subject, content, cc_list, bcc_list, html_content, attachment_list)
# take care the order of arguments, simply you can just send_thread_email(from_email, to_email_list, subject, content)
```

# package `session`
## middleware `DCSessionMiddleware`
only use it in the project `settings.py` file: `session.middlewares.DCSessionMiddleware`.

this middleware provides `request` with an attribute `dc_session`. Visit this attribute is not suggested in project codes, and so no more introduction for it here.
## backend `???`
No introductions here.

