## API Url conventions
Use a url path to identify a resource and pair it with the correct request type to determine its action
### Method Type
- **GET**: Retrieve data, fetch a list or single resource with no side effects
- **POST**: Create or trigger a event, create a new resource or trigger a non CRUD action. Actions that go beyond simply modifying a field 
- **PUT**: Full update, replace the entire object
- **PATCH**: Partial update of a object, changing one or more fields but not the whole object
- **DELETE**: Remove a resource

Example
```
GET /anime/123/ -> Get an anime with id of 123
PATCH /anime/123/ -> Update one or more fields of an anime with id of 123
POST /anime/123/add-two-list/ -> Non CRUD action, im doing something that dosent modify the anime but its relative
PUT /anime/123/ -> Replace the information of an anime with id of 123
DELETE /anime/123/ -> Delete an anime with id of 123
```
## Imports
### Modules over objects
Import modules of a library instead of individual objects for readability and avoid namespace conflicts

Bad
```
from django.http import HttpResponse, HttpResponseRedirect
from django.shortcuts import render, get_object_or_404
```

Good
```
from django import http, shortcuts
```
### Wildcards
Refrain from using the wildcard import as it makes it hard to trackdown where the functionality lives and creates possible namespace conflicts.
Example:
```
from .package import * <- this library has a module called add

from .package_two import * <- this library also has a module called add

*If you call 'add' the compiler wont know which one youre referencing*
```
**Fundementally, its better to be explicit even if its more verbose.**
### Ordering
Follow a standard (PEP8) guideline
- Standard library
- Third part libraries
- Local
## Docstrings / Comments
The first instance of a docstring should complete the following sentence `This function will...`
### Docstrings vs Commenting
- **Docstrings** explain what the function does. They are written for those who want to use that function but are not interested in the implementation details
- **Comments** explain why certain logic was written this way. They are written for those who want understand the implementation details for the purpose of changing or extending it.

## Django 
### Models
#### Field attributes
- `blank` - Okay to omit in forms
- `null` - Okay to for the database to hold null

#### Naming
Model names should be singular and descriptive
```
class Anime(models.Model):

class ComputerPart(models.Model):

class Motherboard(ComputerPart):
```

`DateTimeField`s should generally have the suffix `_at`
```
create_at = DateTimeField()
updated_at = DateTimeField()
```

`DateField`s should generally have the suffix `_date`
```
publishing_date = DateField()
end_of_service_date = DateField()
```

Model query methods should generally have the prefix `get_`
```
def get_related_anime(self):
```

Model setting methods should generally have the prefix `set_`
```
def set_airing_status(self):
```

#### CRUD Methods
Avoid calling a model's `save` method from anywhere but the mutator methods inside the model itself. Similarly, avoid calling the `create` out the model as well.

#### Example
```
class SomeModel(models.Model):
    name = models.CharField(max_length=255)

    # Factories

    @classmethod
    def new(cls, name):
        return cls.objects.create(name=name)

    # Mutators

    def anonymise(self):
        self.name = ""
        self.save()

    def set_name(self, new_name):
        self.name = new_name
        self.save()

    # Queries

    def get_num_apples(self):
        return self.fruits.filter(type="APPLE").count()

    # Properties

    @property
    def is_called_dave(self):
        return self.name.lower() == "dave"
```