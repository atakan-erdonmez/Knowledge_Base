# Primitive Types
- String
- Number
- Bool

# Complex Types
Complex types allow you to group multiple values together into a single variable. It has two versions: Collection type, structural type

## Collection Type
A collection of multiple values grouped together as a single value

- **list(...)**: A sequence of values identified by an index starting with zero.
- **map(...)**: A collection of values, each with a string label identifier (key-value pairs)
- **set(...)**: A collection of unique values without any secondary identifiers or ordering

#### List Usage
```variables.tf
variable "Security_Group"{
	type = "list"
	default = ["sg-35862", "sg-09374", "sg-375847"]
}
```

```main.tf
resource "aws_instance" "Test" {
	ami = asfasdf
	instance_type = sadfasdf
	
	security_groups = "${var.Security_Group}
}
```

#### Map Usage
```variables.tf
variable "AMIs" {
	type = map
	default = {
		us-east-1 = "ami-0fdksskdjf"
		us-east-2 = "ami-asdfkjieas"
	}
}
```

```main.tf
resource "aws_instance" "Test"{
	ami = lookup(var.AMIS, "us-east-1")
	
	# OR, if you are using region as a variable:
	
	ami = lookup(var.AMIS, var.AWS_REGION)
}


```

> **lookup()**: It is a function that gets a value from a map using a key
> lookup(map, key)
## Structural Type
A collection of multiple values of *several district types* grouped together as a single value

- **object(...)**: A collection of values each with their own type
- **tuple(...)**: A sequence of values each with their own type




