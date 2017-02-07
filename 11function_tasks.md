# Adding functions

In the earlier chapter we saw how to take input, update a task, but if you see the code, task4.py, there is a lot of redundant code, what we need to do is write functions to save repeated code.

We first start by defining the `main` function. There is no special significance to the main function, just that we chose to call it as `main`, we can very well choose to call it 'somerandomfunctionasfasdf'.

We push everything _except_ the import statement into the main function.

#### Note: 
If you try to run the file at this point, there would not be any output, the reason for that is that you have declared a function but not **called** it. The interpreter runs the script and it creates a function named "main" and it does nothing. If you want to **run** the main, you have to call it. At the bottom, add `main()` and then try running the file, this time, it'll give _some_ output. 

Now, we create three functions, `add_task`, `remove_task`, and `list_task`. These three would do the respective functions.

The logic of our program should be split between modules. There should be one "controller" module which handles the IO and a supporting library which does something with the data, in that way, we can enable different input sources for the same app. Currently, the input source, which is the command line arguments is deeply coupled with our todo list manager, so if tomorrow, we want to take input from some other source, we have to rewrite the complete application.

For this, what we do is this:

main: handles the IO
add_task(title,content): adds a new task with title and content
list_task(): lists the tasks
remove_task(index): deletes the task of index.

By doing this, the main if-else ladder looks like this

    if command == "add":
        title = args[2]
        content = args[3]
        add_task(title, content)
    elif command == "remove":
        task_id = args[2]
        remove_task(task_id)
    elif command == "list": 
        list_task()
    else:
        print("invalid command!")

Now, if we change the input from command line to say FTP, all we have to do is change the main function, write the FTP input function and call add_task, with the newly fetched title and content. Modularity is really important in programming.

We have no need of declaring the `tasks` variable in the main function, so we remove it.

We also do not want to write "add" every time we refer to the add command, so we define three variables.

    ADD,REMOVE,LIST = "add","remove","list"

So, the next time we want to refer to "add", we will refer to ADD.

This block also changes.

    if command not in (ADD,REMOVE,LIST):
        print("Invalid command\n Use %s/%s/%s"%(ADD,REMOVE,LIST))
        sys.exit(1)

We now try and run the code, and it works!

    ch10 $ python3 tasks4.py
    Invalid arguments!
    ch10 $ python3 tasks4.py list
    |-index----title----content----|
    |-0--new title----new content-|
    |-1--Finish Python book----Working on 10'th chapter-|

The code looks cleaner than tasks4.py, but there is work to do! We can create a module for these three functions and reuse the file object instead of redefining the object in each function.