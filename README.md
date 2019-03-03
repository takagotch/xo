### xo
---
https://github.com/xo/xo

```
CREATE TABLE "SiteContacts" (
  "ContactId" INT NOT NULL,
  "SiteId" INT NOT NULL,
  PRIMARY KEY(ContactId,SiteId),
  FOREIGN KEY("ContactId") REFERENCES "" ( "ContactId" ),
  FOREIGN KEY("SiteId") REFERENCES "" ( "SiteId" )
)


CREATE TABLE users (

);

CREATE OR REPLACE FUNCITON update_modified_column() RETURNS TRIGGER AS $$
BEGIN
  NEW.modified_at = now();
  RETURN NEW;
END;
$$ language 'plpgsql';

CREATE TRIGGER update_users_modtime BEFORE UPDATE ON users FROM EACH EXECUTE PROCEDURE update_modifoed_column();
```

```go
db, err := dburl.Open("file:mydatabase.sqlite3?loc=auto")

db, err := dburl.Open("mysql://user:pass@host/dbname?parseTime=true")

db, err := dburl.Open("mysql://user:pass@host/?parseTime=true&sql_model=ansi")

db, err := dburl.Open("pgsql//user:pass@localhost/dbname")

most RecentUsers, err := models.GetMostRecentUsers(db, 15)
if err != nil {}
for _, user :range users {
  log.Printf("got user: %+v", user)
}


func GetMostRecent{{ .Name }}(db XODB, n int) ([]*{{ .Name }}) {
  const sqlstr = `SELECT` +
      `{{ colnames .Fields "created_at" "modified_at" }}` +
      `FROM {{ $table }}` +
      `ORDER BY created_at DESC LIMIT $1` 
      
  q, err := db.Query(sqlstr, n)
  if err != nil {
    return nil, err
  }
  defer q.Close()
  
  var res []*{{ .Name }}
  for q.Next() {
    {{ $short }} := {{ .Name }}{}
    
    err = q.Scan({{ fieldnames .Fields (print "&" $short) }})
    if err != nil {
      return nil, err
    }
    
    res = append(res, &{{ $short }})
  }
  
  return res, nil
}
```

```sh
go get -u golang.org/x/tools/cmd/goimports

go get -u github.com/xo/xo
go get -tags oracle -u github.com/xo/xo

cd $GOPATH/src/path/to/project

mkdir -p models

xo pgsql://user:pass@host/dbnme -o models

mkdir -p mssqlmodels
xo mysql://user:pass@host/dbname -o mssqlmodels --template-path /path/to/custom/templates

xo pgsql://user:pass@host/dbname -N -M -B -T AuthorResult -o models/ << ENDSQL

go build ./models/
go build ./mssqlmodels/

go install ./models/
go install ./mssqlmodels/

xo --help

cd $GOPATH/src/path/to/my/project

mkdir -p templates

cp "$GOPATH/src/github.com/xo/o/templates/*" templates/

rm templates/*.go

vi tempaltes/postgres.*.tpl.go

xo pgsql://user:pass@host/db -o models --template-path templates

go generate && go build

tee -a gen.go << ENDGO
go generate
git add templates gen.go && git commit -m 'Adding custom xo templates for models'

xo pgsql://user:pass@host/db -o models --ignore-fields created_at modified_at

cd $GPATH/path/to/project
mkdir -p templates
cp $GOPATH/src/github.com/xo/xo/tempaltes/* tempaltes/

vi templates/postgres.typ.go.tpl

xo pgsql://user:pass@localhost/dbname -o models --template-path templates/
xo --escape-all 'mysql://user:pass@host/?parseTime=true&sql_mode=ansi' -o models
xo 'mysql://user:pass@host/dbname?parseTime=true' -o models

xo 'file:mydatabase.sqlite3?loc=auto' -o models

go get -u github.com/xo/xo

sudo aptitude install alien

sudo alien -i oracle-instantclient-12.1-basic-*.rpm
sudo alien -i oracle-instantclient-12.1-devel-*.rpm
sudo alien -i oracle-instantclient-12.1-sqlplus-*.rpm

go get -u github.com/xo/xo

sudo cp $GOPATH/src/github./xo/xo/contrib/oci8.pc /usr/lib/pkgconfig/
go get -u gopkg.in/rana/ora.v4
go install -tags oracle github.com/xo/xo

go get -tag oracle -ugithub.com/xo/xo
```


