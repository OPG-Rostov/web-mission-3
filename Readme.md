# Часть 0
https://supabase.com/dashboard/project/yfejhssvkdzjihkizhhi

# Часть 1
https://buildship.app/remix/64100406-8f63-47f5-b6ff-d06ffb290d13
![image](https://github.com/user-attachments/assets/f661cc54-6bb8-4120-9cf3-08749b7cbe91)

# Часть 2
https://buildship.app/remix/612fc71e-a508-4127-9f19-460a79348511
![image](https://github.com/user-attachments/assets/75e4641c-b01a-4d5f-af7f-9c8e3cf2d3a7)

 # Часть 3
Запрос 1. Получить список юзернеймов пользователей
 SELECT username FROM users

Запрос 2. Получить количество отправленных сообщений каждым пользователем
 SELECT u.username, COUNT(m.id) AS number_of_sent_messages
 FROM users u
 LEFT JOIN messages m ON u.id = m.from
 GROUP BY u.username;

Запрос 3. Получить пользователя с самым большим количеством полученных сообщений и само количество:
 SELECT username, COUNT(*) AS "number of received messages"
 FROM messages
 JOIN users ON messages.to = users.id
 GROUP BY username
 ORDER BY COUNT(*) DESC
 LIMIT 1;

Запрос 4. Получить среднее количество сообщений, отправленное каждым пользователем
 SELECT username, AVG(cnt) AS "average number of sent messages"
 FROM(
 SELECT messages.from, COUNT(*) AS cnt
 FROM messages
 GROUP BY messages.from
 ) AS message_count
 JOIN users ON message_count.from = users.id
 GROUP BY username;
