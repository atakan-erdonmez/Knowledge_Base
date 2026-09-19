- `depends_on`: Used to explicitly define dependencies between resources
- `count` and `for_each`: Allow the creation of multiple resources of the same type without having to declare separate resource blocks.
- `provider`: Allows defining explicitly which provider to use with a specific resource.


#### Lifecycle meta-arguments
- `create_before_destroy`: Prevent TF's default behavior of destroying before creating.

> When there is an update in the resource that cannot be executed in place, TF's default action is destroy old first, then create a new resource.


- `prevent_destroy`: Terraform exits with an error if the planned changes would lead to the destruction of the resource marked with this.
- `replace_triggered_by`: Replaces the resource when any of the referenced items change.
- `ignore_changes`: We can provide a list of attributes that should not trigger an update when *modified outside TF.*


**Usage**:
```
resource "aws_instance" "my_instance" {
	ami = "asfdasdf"
	instance_type = "asdfasdf"
	
	lifecycle {
		create_before_destroy = true
		ignore_changes = [ tags ]
	}
}
```