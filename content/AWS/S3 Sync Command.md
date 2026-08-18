---
link:
  - "[[S3]]"
  - "[[AWS CLI]]"
---
The `aws s3 sync` command is a powerful utility provided by the AWS Command Line Interface (CLI) that synchronizes the contents of a source location with a destination location.

It works recursively by default, comparing the source and destination to determine which files are new, modified, or missing, and then copying only the differences.

## 1. Supported Sync Pathways

The command is highly versatile and can synchronize data across three different pathways:

- **Local to S3 (Upload):** Syncs a local directory up to an S3 bucket.
- **S3 to Local (Download):** Syncs an S3 bucket down to a local directory.
- **S3 to S3 (Copy):** Syncs objects directly between two different S3 buckets (even across different AWS accounts or regions).

## 2. Core Syntax

The basic syntax for the command is:

Bash

```
aws s3 sync <source> <destination> [flags]
```

### Common Examples

- **Uploading a local folder:**

    ```
    aws s3 sync /path/to/local/folder s3://my-bucket-name/backup/
    ```

- **Downloading a bucket:**

    ```
    aws s3 sync s3://my-bucket-name/backup/ /path/to/local/folder
    ```

- **Syncing between two buckets:**

    ```
    aws s3 sync s3://source-bucket s3://destination-bucket
    ```

## 3. How `sync` Determines What to Copy

Unlike `aws s3 cp` (which blindly copies everything you tell it to), `aws s3 sync` is smarter. It examines the properties of the files and will only copy a file if:

1. The file size is different between the source and destination.
2. The last modified time of the source file is newer than the file in the destination.
3. The file does not exist at all in the destination.

## 4. Crucial Flags to Know

- **`--delete`**: By default, if a file is deleted from the _source_, `s3 sync` will **not** delete it from the _destination_. Adding the `--delete` flag tells AWS to remove any files in the destination that no longer exist in the source.

- **`--exclude`**: Allows you to skip certain files or patterns (e.g., `--exclude "*.log"`).

- **`--include`**: Used in conjunction with exclude to selectively add files back (e.g., `--exclude "*"` `--include "*.pdf"` will exclude everything _except_ PDFs).

- **`--dryrun`**: Displays a preview of the operations (what will be copied, deleted, or updated) without actually executing the command. This is highly recommended when testing large changes or using the `--delete` flag.