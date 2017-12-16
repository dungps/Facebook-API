# Facebook API

## Table content

1. [Count message sent](#count-message-sent)
2. [Delete message](#delete-message)
3. [List of friends](#list-of-friends)
4. [List of blocked](#list-of-blocked)
5. [List of friend requests](#list-of-friend-requests)
6. [Search people](#search-people)
7. [Search page](#search-page)
8. [Search group](#search-group)
9. [List of pages and groups you are administrator](#list-of-pages-and-groups-you-are-administrator)
10. [List of groups your are joined](#list-of-groups-you-are-joined)
11. [Count page likes](#count-page-likes)
12. [Send message by list UID](#send-message-by-list-uid)
13. [Invite to like a page](#invite-to-like-a-page)
14. [Invite to an event](#invite-to-an-event)
15. [Comment Tag](#comment-tag)
16. [Share post to friend's wall](#share-post-to-friend-s-wall)
17. [Share and tag friends](#share-and-tag-friends)
18. [Share post to group](#share-post-to-group)

## Content

### 1. Count message sent
```
https://graph.facebook.com/me/threads?limit=50&access_token={access_token}
```

### 2. Delete message
```
https://graph.facebook.com/{message_id}?method=delete&access_token={access_token}
```

### 3. List of friends
```
https://graph.facebook.com/fql?q=SELECT+uid,+name,+friend_count,+subscriber_count+FROM+user+WHERE+uid+IN+(SELECT+uid2+FROM+friend+WHERE+uid1+=+me())++ORDER+BY+rand()+LIMIT+5000&access_token=
```

### 4. List of blocked
```
https://graph.facebook.com/fql?q=SELECT+id,+can_post,+name+FROM+profile+WHERE+id+IN+(SELECT+uid2+FROM+friend+WHERE+uid1+=+me())+AND+name+=+"Facebook+User"+ORDER+BY+rand()+LIMIT+5000&access_token={access_token}
```

### 5. List of friend request
```
https://graph.facebook.com/?access_token={access_token}&batch=[{"name":+"friendrequests",+"method":"GET",+"relative_url":"v1.0/me/friendrequests?limit=5000"},+{"method":"GET",+"relative_url":"fql?q=SELECT+uid,+name,+mutual_friend_count,+sex+FROM+user+WHERE+uid+IN+({result=friendrequests:$.data[*].from.id})"}]&amp;include_headers=false&amp;method=post
```

### 6. Search people
```
https://graph.facebook.com/search?type=user&q={key_word}&limit={limit}&fields=id,name&access_token={access_token}
```

### 7. Search page
```
https://graph.facebook.com/search?type=page&q={key_word}&limit={limit}&=id,name,icon&access_token={access_token}
```

### 8. Search group
```
https://graph.facebook.com/search?type=group&q={key_word}&limit={limit}&=id,name,icon&access_token={access_token}
```
