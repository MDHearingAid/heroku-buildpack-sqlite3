## heroku-buildpack-sqlite3

Download and install sqlite3 for use with your app.

### Add this buildpack to your project.

#### Via CLI

```shell
$ heroku buildpacks:set mdhearing/sqlite3
```

#### Via app.json

```json
{
  "environments": {
      "buildpacks": [
        {
          "url": "mdhearing/sqlite3"
        }
      ]
    }
  }
}
```

> Alternatively, you can use the full URL of the buildpack `https://github.com/MDHearingAid/heroku-buildpack-sqlite3.git`.

### Define your own SQLite binary URL

By default, this buildpack will load the SQLite binary located at `https://s3.amazonaws.com/sqlite3-heroku/sqlite3.tar.gz`. Add URL to the `SQLITE3_URL` environment variable in your app to load the SQLite binary of your choosing.

```shell
$ heroku ci:config:set SQLITE3_URL=https://example.com/sqlite3.tar.gz --pipeline=my-pipeline
```

or

```shell
$ heroku ci:config:set SQLITE3_URL=https://example.com/sqlite3.tar.gz --app=app
```

The URL should point to a publicly accessible `tar.gz` archive that contains the SQLite binary named `sqlite3`.

#### Download SQLite builds

1. Go to https://www.sqlite.org/download.html
2. Download the archive labeled as "Precompiled Binaries for Linux"
3. Unpack the archive
4. Grab the `sqlite3` binary from the package

```shell
$ curl -O https://www.sqlite.org/2024/sqlite-tools-linux-x64-3450200.zip
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 10.4M  100 10.4M    0     0  8823k      0  0:00:01  0:00:01 --:--:-- 8864k
$ unzip sqlite-tools-linux-x64-3450200.zip
Archive:  sqlite-tools-linux-x64-3450200.zip
  inflating: sqlite3
  inflating: sqldiff
  inflating: sqlite3_analyzer
$ tree
.
├── sqldiff
├── sqlite-tools-linux-x64-3450200.zip
├── sqlite3
└── sqlite3_analyzer

0 directories, 4 files
```
