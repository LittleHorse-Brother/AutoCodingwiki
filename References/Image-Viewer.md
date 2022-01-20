
This configuration will add an API to download image content. For image configuration in some entities, we often have an option of system image or custom image. So, we provide some configuration to decide what image content should be displayed. Because entity’s field is the actual storage structure in the corresponding database, we offer this configuration that will give a friendlier API.

- [EntityUniqueName](#EntityUniqueName)
- [Name](#Name)
- [IsAuthenticationRequired](#IsAuthenticationRequired)
- [FieldForCustomImage](#FieldForCustomImage)
- [FieldForIsUseCustomImage](#FieldForIsUseCustomImage)
- [FieldForReferencingSystemImage](#FieldForReferencingSystemImage)


## EntityUniqueName

`string`

Required

The name of a specific entity. Indicates which entity the current **Image Viewer** configuration belongs to.

## Name

`string`

Required

The name of the current API will be used in the URL.


## IsAuthenticationRequired

`bool`

Default: `false`

Indicates whether the API needs to be authenticated. False means that anonymous users can download this image from the url, while true means that only authenticated users can download this image.

## FieldForCustomImage

`string`

Required

The name of field for custom image in the entity. Should be an image type field.

## FieldForIsUseCustomImage

`string`

Default: `""`

The name of field for determining whether to use custom image in the entity. Should be a boolean field.

## FieldForReferencingSystemImage

`string`

Default: `""`

The name of field that refers to the system image in the current entity. Should be a reference field.

---

# How to configure

For agent avatar, we have 3 fields to determine what the avatar should display. The 3 fields are `systemAvatarId`, `ifCustomizeAvatar` and `customizeAvatar`. And we want the avatar's api endpoint should be `/agents/{id}/avatar`. Therefore, we will set the properties for each fields as following:
  - entityUniqueName: `agent`
  - name: `avatar`
  - fieldForCustomImage: `customizeAvatar`
  - fieldForIsUseCustomImage: `ifCustomizeAvatar`
  - fieldForReferencingSystemImage: `systemAvatarId`

After these configurations are completed, there will be an additional property `avatar` under the agent entity. The value of this property will be a url to download this image. It will take a hash value in query (version). 

![agent-avatar.png](/.attachments/agent-avatar-bf7265f0-1295-4d26-b40b-9d6f7d594982.png)

The front-end can directly use this url to display the image. And the server will decide to display custom image or system image according to the actual configuration.
