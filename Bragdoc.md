# In progress
```dataview
TABLE
    join(filter(file.etags, (tag) => contains(tag,"action")), " ") AS Action,
    join(filter(file.etags, (tag) => contains(tag,"context")), " ") AS Context,
    join(filter(file.etags, (tag) => contains(tag,"skill")), " ") AS Skill,
    priority AS Priority,
    length(filter(file.tasks, (task) => !task.completed)) as Pendings
FROM "PicPay/Bragdoc"
WHERE
    file != this.file AND
    status = "in progress"
SORT priority
```

# Pending
```dataview
TABLE
    join(filter(file.etags, (tag) => contains(tag,"action")), " ") AS Action,
    join(filter(file.etags, (tag) => contains(tag,"context")), " ") AS Context,
    join(filter(file.etags, (tag) => contains(tag,"skill")), " ") AS Skill,
    priority AS Priority,
    length(filter(file.tasks, (task) => !task.completed)) as Pendings
FROM "PicPay/Bragdoc"
WHERE
    file != this.file AND
    status = "pending"
SORT priority
```

# Done
```dataview
TABLE
    join(filter(file.etags, (tag) => contains(tag,"action")), " ") AS Action,
    join(filter(file.etags, (tag) => contains(tag,"context")), " ") AS Context,
    join(filter(file.etags, (tag) => contains(tag,"skill")), " ") AS Skill,
    priority AS Priority,
    length(filter(file.tasks, (task) => !task.completed)) as Pendings
FROM "PicPay/Bragdoc"
WHERE
    file != this.file AND
    status = "done"
SORT priority
```

# Tarefas
```dataview
TASK
FROM "PicPay/Bragdoc"
GROUP BY file.link
```