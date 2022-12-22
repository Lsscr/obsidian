<%*
const {autoprop} = this.app.plugins.plugins["metaedit"].api;
tR = `#tasks 
Complete:: 0
Project::
Status:: ${await autoprop("Status")}
Priority:: ${await autoprop("Priority")}
Due Date::

Complete:: 0
Energy::
Estimated Time::

Total:: 1
Complete:: 0
Incomplete:: 1

---

- [ ] <% tp.file.cursor() %>`
 %>