# Database code for the DB Forum, full solution!
# Second Version of initial

import datetime
import psycopg2
import bleach

DBNAME = "forum"

def getPosts():
  """Return all posts from the 'database', most recent first."""
  db = psycopg2.connect(database=DBNAME)
  c = db.cursor()
  c.execute("select content, time from posts order by time desc")
#  posts = [{'content': str(bleach.clean(row[1])), 'time': str(row[0])}
#  for row in c.fetchall()]
  posts = c.fetchall()
#  posts = [{'content': str(row[1]), 'time': str(row[0])} for row in #c.fetchall()]
#  posts.sort(key=lambda row: row['time'], reverse=True)

#  for item in range(0, len(posts)):
#    for key in posts[item]:
#        if(key == 'content'):
#            posts[item][key] = str(bleach.clean(posts[item][key]))
  db.close()
  return posts

def addPost(content):
  """Add a post to the 'database' with the current timestamp."""
  db = psycopg2.connect(database=DBNAME)
  c = db.cursor()
  cleanContent = bleach.clean(str(content))
  c.execute("insert into posts (content) values (%s)", (cleanContent,))
#  cleanContent = bleach.clean(content)
#  c.execute("insert into posts values (%s)", (bleach.clean(content),))
  # good
  db.commit()
  db.close()
