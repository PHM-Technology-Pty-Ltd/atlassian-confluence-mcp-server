# Confluence MCP Server

Domain language for the Atlassian Confluence MCP server — terms agents and contributors share when talking about Confluence content operations.

## Language

**Attachment**:
A binary file stored on a Confluence page (or comment) as child content, identified by filename/`title` within that parent.
_Avoid_: File upload payload, media asset, blob

**Host file path**:
An absolute filesystem path on the machine running the MCP server, used as the sole source when uploading an attachment.
_Avoid_: Relative path, base64 body, content string, remote URL

**Attachment upsert**:
Uploading a file whose filename already exists on the target container creates a new attachment version rather than failing or creating a duplicate title.
_Avoid_: Create-only upload, separate update tool, force-overwrite without versioning

**Client attachment size limit**:
The MCP host’s configured maximum bytes allowed to read from a host file path before attempting upload; independent of Confluence’s own Attachment Maximum Size setting.
_Avoid_: Server-discovered attachment max, Jira attachment/meta

**Attachment container**:
The Confluence content that owns an attachment — either a page or a comment (both expose the same child-attachment REST resource).
_Avoid_: Parent only as page, attachment host
