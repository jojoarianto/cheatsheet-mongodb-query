# Create user on spesific database

```bash
# create user
db.createUser(
    {
        "user": "iriantogo",
        "pwd": "mypassword",
        "roles": [
            {role: "userAdmin", db:"sibiti"}
        ]
    }
)

# give more role to user
db.grantRolesToUser(
   "iriantogo",
   [ { role: "readWrite", db: "mydatabase" } ],
   { w: "majority" , wtimeout: 4000 }
)

# see user spec
db.getUser("iriantogo");
```

referensi
https://www.guru99.com/mongodb-create-user.html
