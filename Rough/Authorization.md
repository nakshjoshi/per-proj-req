Authorization:to identify(CRUD opereation,  done using generating JWT tokens, cookies)
Authencatikon: to give permission
Types of Authorization:
1. RBAC: very small scale, Assigns permissions based on predefined roles 
(admin, editor, viewer). → Example: In a personal blog, editors can create/edit posts, users can 
only read/comment. → Limitation: Not suitable for platforms where permissions vary per 
resource (e.g., blogs owned by different users).

2. Fine Grained RBAC: done at resouces level and not platform level ->for every action we need to quert the table and see user config
3. ABAC: we match resouces attribute === user attrubute basically, control over resources is deciede thoruhg attributees assigned \:
4. Policy Based AC: present on cloud infrastructre like AWS, set policy fot resouces user and team(microservice)
5. ReBAC9realtion based: Nesting/parent-child relation decides the access control to top level and botton level users
6. Google Zanzibar: Paper presented bt google, consistent google auth system based on graoph algo
7. OpenFGA: open sources kinda look alike of google zanzibar, donated by google to CNCF follow relationa based AC using graph 