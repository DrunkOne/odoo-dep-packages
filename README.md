Quick fix installation scripts for Odoo. Only looks to address the ```requirements.txt``` file.

```
  Getting requirements to build wheel ... error
  error: subprocess-exited-with-error
```
Issue is addressed here (https://github.com/odoo/odoo/issues/187021)

As addressed by @b-enoit-be (Nov13,2024) issue occured since recent publication of [Cython==3.1.0a1](https://github.com/cython/cython/releases/tag/3.1.0a1). Gevent requires ```Cython==3.0a9``` (gevent-requirements)[https://github.com/gevent/gevent/blob/21.8.0/pyproject.toml#L25C7-L25C22]

Causing compilation issues. Skipping ```gevent==21.8.0``` and appending environment comparator fixes this issue during package installation script.

Also noted by @ryumada that skipping ```greenlet==1.1.2``` for later version ```greenlet==2.0.2``` also fixes this issue.

