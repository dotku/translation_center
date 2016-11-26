#Translation Center
A simple translation manage tool

## Database Design

```mysql
Create Table project (
	project_id int not null auto_increment,
  project_name varchar(80) not null,
  primary key(project_id)
);

CREATE Table tag (
  tag_id int not null auto_increment,
  tag_name varchar(80) not null,
  primary key(tag_id)
);

CREATE Table tran (
  tran_id int not null auto_increment,
  tran_string varchar(800) not null,
  primary key(tran_id)
);

CREATE Table lang (
  lang_id int not null auto_increment,
  lang_name varchar(80) not null,
  primary key(lang_id)
);

Create Table tran_rel (
  tran_rel_id int not null auto_increment,
  tag_id int,
  tran_id int,
  lang_id int,
  primary key(tran_rel_id),
  FOREIGN KEY (tag_id) REFERENCES tag(tag_id),
  FOREIGN KEY (tran_id) REFERENCES tran(tran_id),
  FOREIGN KEY (lang_id) REFERENCES lang(lang_id)
);

Create Table log_publish (
  log_publish_id int not null auto_increment,
  target_path varchar(800) not null,
  versionId timestamp default current_timestamp,
  primary key (log_publish_id)
);
```

## Usage Flow Chart

### import
1. Create translation file, refer to angular-translation for [the format](https://angular-translate.github.io/)
2. Import to the system
3. Save and publish to the target file path

### modify
you can modify by login to the MySQL database

### publish
it will generate a json file based on angular-translation format.  
\* in the future, we are going to generate the file by json template
