# Jupyter

## [SSH Tunneling](http://jupyter-notebook.readthedocs.io/en/latest/public_server.html#notebook-server-security)

On the remote machine, generate jupyter config

```
jupyter notebook --generate-config
```
This will generate a config python file as `~/.jupyter/jupyter_notebook_config.py`. 
Edit this file as needed, for instance, `c.NotebookApp.password`, `c.NotebookApp.port = 8889`, `c.NotebookApp.ip = '127.0.0.1'`.
Then, prepare password within `jupyter console`

```
from notebook.auth import passwd; passwd()
```

Copy the generated string, e.g. `'sha1:67c9e60bb8b6:9ffede0825894254b2e042ea597d771089e11aed'` and paste into 

```
c.NotebookApp.password = 'sha1:67c9e60bb8b6:9ffede0825894254b2e042ea597d771089e11aed'   
```

On the local machine, add an alias in `~/.profile` or `~/.bash_profile`

```
alias sshtf="ssh -N -L localhost:8890:localhost:8889 $TFBOX"
```

where `N` for no command for tunneling only and `L` for local port forwarding (from local to remote, or attach remote resource to local port).

Once this is set up. Go to the remote end,

```
jupyter notebook --no-browser
```

And on the local end, `sshtf` to launch the connection. Now, it is ready to open the browser at `localhost:8890` for remote Jupyter notebook

## Themes and Styles

Overwrite theme and configuration before start jupyter notebook

```
jt -t chesterish -f ubuntu -fs 10 -cellw 1100 -lineh 120 -tf roboto -tfs 10
```

Modify the coloration etc.
Install `less`

```
sudo npm install -g less
chmod -R 755  /usr/lib/node_modules/
```

After modification of `.less` file, compile it into something

```
lessc styles.less styles.css
```


