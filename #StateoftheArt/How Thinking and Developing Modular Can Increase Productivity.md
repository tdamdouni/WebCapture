# How Thinking and Developing Modular Can Increase Productivity

_Captured: 2015-12-01 at 14:10 from [designreviver.com](http://designreviver.com/articles/how-thinking-and-developing-modular-can-increase-productivity/)_

When we have one few too many clients, we panic and begin to cut corners to squeeze in as many clients as we can into our schedule, and we end up working nights and weekends with buggy results. What if there is a way to save time and still manage the same amount of clients if not more?

Creating modular components is a step closer to reaching that goal, you can have 10, 20, 30, or even 40% if not more complete already with just several minutes of piece work.

#### How Does Developing With Modularity in Mind Work?

![](http://designrevivercom.c.presscdn.com/wp-content/uploads/2010/07/thinkmodular-1.jpg)

Developing with modularity in mind means everything that you can develop that can work on its own without the requirement of being laced with its parent to function properly. For example, let us say a client needs a content management system developed in PHP. Off the top, we already know we will need to develop a pagination system, a MySQL Class, and a template system.

An advanced pagination system can take few hours to perfect, a good well equipped MySQL class can take an hour or two, and a full-fledged template system can take several hours if not a few days to get it right. However, if these components are developed to be modular, you will only spend the time developing them once, and only several minutes integrating them into any other project, saving you hours and days of work.

To provide a real world example; a recent client I had needed a system that displays his inventory from his database. I quickly grabbed my already developed pagination class and MySQL class, restructured the provided MySQL tables, and retrieved the inventory paginated. The entire project took me thirty minutes to complete where it would have taken me several hours to complete if I had to start from scratch.

Therefore, spending the time to develop quality modular components increases your productivity and saves you time. Additionally, reinventing the "wheel" is always an action unnecessary and unneeded, thus being able to copy and paste modular components into many of your projects is a lifesaver.

#### How to Develop Modular Components

Developing modular components is all about the structural design, keeping it unattached to a specific project you are developing. The first step in creating a modular component is to think modular. Let us look at glue, it is a substance that mends and works on many items you need it for, however, it does not need your items to properly function as it functions alone. This is exactly how modularity works and the way these components should be developed.

In order to help grip this concept better, we will do a run down on a modular component as well as have it available for **download free** at the end of this article to have a go at it yourself.

The modular component we will be looking at is an advanced PHP MySQL Class, which makes connecting to a database and running queries easy. Let's look at the constructor of this class:
    
    
        function __construct($db_host, $db_user, $db_pass, $db_name, $db_prefix)
        {
           //define 'em all!
           $this->host   = $db_host;
           $this->user   = $db_user;
           $this->pass   = $db_pass;
           $this->name   = $db_name;
           $this->prefix = $db_prefix;
        }
                

The constructor in this case gathers all the necessary information so that the methods of this class properly function.  
Therefore, allowing the component to work seamlessly with your project while keeping the component separate and modular.

In order to understand how this class works, we will look at a couple of its methods starting with the connect method.
    
    
        protected function connect()
        {
           $this->db = mysql_connect($this->host, $this->user, $this->pass) or die(mysql_error()."".$this->db);
               //check if we have connected, otherwise run this function again
    
           if(!$this->db)
        {
           $this->connect();
                        }
    
             //since we're connected, let's select the db
                else
        {
           $this->db = mysql_select_db($this->name, $this->db) or die(mysql_error()."".$this->db);
               return $this->db;
                        }
                    }
                

As shown above, the connect method is a protected method that creates a connection with MySQL and selects the database. The reason it is inaccessible outside of this class is that this method runs automatically by other methods within the class; hence, you do not need to call it. Another method we will look at is the select method, which builds a select query based on the information you provide via its parameters:
    
    
        public function select($table, $fields="*", $conditions=0, $options=array())
        {
               //check if we have a db connection
          if(!$this->db)
        {
          $this->connect();
                        }
    
        $query = "SELECT ".$fields." FROM ".$this->db_prefix.$table."";
           if($conditions !=0)
         {
        $query .= " WHERE ".$conditions;
                        }    
    
           if(isset($options['order_by']))
         {
    
         $query .= " ORDER BY ".$options['order_by']."";
           if(isset($options['order_dir']))
    
          {
         $query .= " ".strtoupper($options['order_dir']);
                            }
                        }
            if(isset($options['limit_start']) && isset($options['limit']))
          {
         $query .= " LIMIT".$options['limit_start'].",".$options['limit'];
                        }
    
            elseif(isset($options['limit']))
          {
         $query .= " LIMIT ".$options['limit'];
                        }
    
            if(!$this->db)
          {
         $this->connect();
                        }
    
           return $this->query($query);
                    }

While it may seem to be easier to build the query yourself, this method retains the integrity of your system and keeps your projects tidy, and as a bonus, it makes creating queries for your client a lot easier when they modify their script. Additionally, integrating security measures within these methods means that those security measures will be applied to all the queries you run, good for filling in the gaps that you may have missed.

#### Download the MySQL Class

This MySQL Class is for demonstration and learning purposes only. **[Click to Download.](http://designrevivercom.c.presscdn.com/wp-content/uploads/2010/07/mysql_class.zip)**
