1. Dockerize the app.

	- Redis/Memcache

	- MySQL/Postgres

1. Should use soft delete for users. 

	- So that if user has been soft deleted, the message still can display.

	- Achieve it by adding a soft delete migration, and using SoftDeletes trait in model.

1. Should have foreign key.

	- Data integrity.

1. Messages parent_id can be default to 0, to represent as top ancester. 
	
	- because that column is not null. If turn off not null, the index won't work.

	- You have to manually set parent_id, when initialize the first message, if no default. But it makes sense to make it 0, because every message is "reply-able".

1. Section, Topic and Messages, needs delete on cascade.

	- It doesn't make sense to have an orphan message without topic or section.

1. Delete Message, also needs to delete all descendants.

	- Achieve it by Model Event, or just use boot() function inside Model.

1. Laravel Passport for API login

1. Seed a master user.

1. Can add some cache for huge amount of messages. (profiling first use Laravel Debugbar.)

	- Use Redis.

	- Crucial to have immediate data?

	- Cache::remember() and Cache::forget()

1. Can cache Avatar if fetched from AWS S3.

1. $table->engine = "InnoDB"

1. You should create an index on a column in any of the following situations:

	1. The column is queried frequently

	1. Foreign key column(s) that reference other tables
	
	1. A unique key exists on the column(s)

1. reduce `max_sort_length` for DB. when sort `body` as Alphabetic.

1. use length-index on `body`.

1. Resource can be extended with more data. eg: user_id can be UserResource.