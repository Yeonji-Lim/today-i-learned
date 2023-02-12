# PyMySQL

connect ~ insert ~ close의 과정 예시

```python
g = Github(access_token)

o = get_org(g)

con = pymysql.connect(host='localhost', user='github_crawler', password='crawling', db='github_crawling', charset='utf8')

cur = con.cursor()

for t in o.get_teams():
	sql = 'insert into Team(id, name) values(%s, %s)'
	cur.execute(sql, (int(t.id), t.name))

con.commit()

con.close()
```

