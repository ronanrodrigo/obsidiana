<%* let title = tp.file.title
  if (title.startsWith("Untitled")) {
    tp.file.rename(tp.file.creation_date("YYYY-MM-DD"));
  } 
-%>
<< [[<% tp.date.now("YYYY-MM-DD", -1) %>]] | [[<% tp.date.now("YYYY-MM-DD", 1) %>]] >>

- [ ] Verificar compromissos agendados
- [ ] Organizar as tarefas do board e atualizar o Bragdoc
<%*
  if (tp.date.now("e") === 0) {
    tR += "- [ ] Escolher atuações principais da semana"
    tR += "- [ ] Comunicar atuações principais da semana"
  } else {
    tR += "- [ ] Escolher atuação principal do dia"
  }
  
%>

# Tarefas d'outrora
```dataview
TASK
FROM "Daily Plans"
WHERE completed = false AND
    text != "Foo" AND
    file != this.file
GROUP BY file.link
```

# Outras tarefas
```dataview
TASK
FROM "PicPay"
WHERE completed = false
GROUP BY join(list(replace(file.folder,"PicPay/",""), file.link), "/")
```