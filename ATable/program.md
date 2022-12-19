```dataviewjs
function projectTracker(dv, query) {
    let searchPagePaths = dv.pages(query).file.path
    
    for(let i=0; i < searchPagePaths.length; i++){
        if(dv.page(searchPagePaths[i]).Total){
                    let title = dv.page(searchPagePaths[i]).Title;
                    let total = dv.page(searchPagePaths[i]).Total;
                    let status = ((dv.page(searchPagePaths[i]).Completed / dv.page(searchPagePaths[i]).Total) * 100).toFixed();
                    let suffix = dv.page(searchPagePaths[i]).Suffix;
                    const progress = "![pb|500](https://progress-bar.dev/" + status + "/?scale=" + "100" + "&title=" + title + "&width=400)";
                    dv.paragraph(progress);
                    dv.paragraph("<br>");
        }
    }
} 

projectTracker(
    dv,
    "#projects"
)
```
# 查询列表

```dataview
TABLE tags,status,date from #JavaScript & #前端 sort date desc
```