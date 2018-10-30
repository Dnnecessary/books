```
创建数据库：    Bundle  exec  rake  db:create  

development:
  adapter: mysql2
  database: test_migration
  username: root
  password: 123456
  host: localhost
  ```


  ```
  新建users表： bundle  exec  rails  generate  migration  create_users

对应的migration：
class CreateUsers < ActiveRecord::Migration[5.0]
  def up
    create_table :users do |t|
      t.string :title
      t.string :name
      t.string :age
      t.string :maed
    end
  end


  def down
    drop_table :users
  end
end
```


回滚 `bundle exec rake db:rollback`  执行`down` 方法
在 `bundle exec rake db:migrate`    执行 `up` 方法





```
新建name列 :  bundle  exec   rails   generate  migration  add_column  :users,  :name,  :string

class AddColumn < ActiveRecord::Migration[5.0]
  def up
    add_column :books, :nameuser, :string
  end

  def down
    remove_column :books, :nameuser
  end
end
```    


```
删除name列:   bundle  exec  rails  generate  migration  remove_column  :books,  :name
```



```
删除fruits表:  bundle exec rails generate migration drop_table :fruits

class DropTable < ActiveRecord::Migration[5.0]   删除表
  def up
    drop_table :fruits
  end

  def down
    create_table :fruits
  end
end

```


```
修改列名

bundle exec rails generate migration rename_age_to_my

rename_ 原列名 _to_ 新的列名
