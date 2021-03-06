### group Snapshots

A snapshot is a full-volume copy stored in our secure data centers.

#### Snapshots [/snapshots]

##### Create a snapshot [POST]

Create a new snapshot.

The response is an object that has a key called `snapshot`. This key contain a standard `snapshot` object.

+ Attributes
    + name: `snapshot-0-1` (required, string) - Human readable snapshot name
    + organization: `000a115d-2852-4b0a-9ce8-47f1134ba95a`(required, string) - Unique organization identifier
    + volume_id: `701a8946-ff9d-4579-95e3-1c2c2d0f892d`(required, string) - Unique volume identifier

+ Request (application/json)

    + Body

            {
                "name": "snapshot-0-1",
                "organization": "000a115d-2852-4b0a-9ce8-47f1134ba95a",
                "volume_id": "701a8946-ff9d-4579-95e3-1c2c2d0f892d"
            }

+ Response 200 (application/json)

        {
          "snapshot": {
            "base_volume": {
              "id": "701a8946-ff9d-4579-95e3-1c2c2d0f892d",
              "name": "vol simple snapshot"
            },
            "creation_date": "2014-05-22T12:10:05.596769+00:00",
            "id": "f0361e7b-cbe4-4882-a999-945192b7171b",
            "name": "snapshot-0-1",
            "organization": "000a115d-2852-4b0a-9ce8-47f1134ba95a",
            "size": 10000000000,
            "state": "snapshotting",
            "volume_type": "l_ssd"
          }
        }


##### List all snapshots [GET]

List all snapshots associate with your account

The response is an object that has a key called `snapshots`. This key contain an array of snapshot objects each of which contain the standard `snapshot` attributes.

+ Response 200 (application/json)

        {
          "snapshots": [
            {
              "base_volume": {
                "id": "09a4184c-733b-43c8-99c3-f1dde30536fe",
                "name": "vol simple snapshot"
              },
              "creation_date": "2014-05-22T12:11:06.055998+00:00",
              "id": "6f418e5f-b42d-4423-a0b5-349c74c454a4",
              "name": "snapshot-0-1",
              "organization": "000a115d-2852-4b0a-9ce8-47f1134ba95a",
              "size": 10000000000,
              "state": "snapshotting",
              "volume_type": "l_ssd"
            },
            {
              "base_volume": {
                "id": "09a4184c-733b-43c8-99c3-f1dde30536fe",
                "name": "vol simple snapshot"
              },
              "creation_date": "2014-05-22T12:13:09.877961+00:00",
              "id": "c6ff5501-eb35-44b8-aa01-8777211a830b",
              "name": "snapshot-0-2",
              "organization": "000a115d-2852-4b0a-9ce8-47f1134ba95a",
              "size": 10000000000,
              "state": "snapshotting",
              "volume_type": "l_ssd"
            }
          ]
        }

#### Snapshot [/snapshots/{snapshot_id}]

+ Parameters
    + snapshot_id: `6f418e5f-b42d-4423-a0b5-349c74c454a4`(required, string) - Snapshot unique identifier

##### Retrieve a snapshot [GET]

List an individual snapshot

The response is an object that has a key called `snapshot`. This key contain a standard `snapshot` object.

+ Response 200 (application/json)

        {
          "snapshot": {
            "base_volume": {
              "id": "09a4184c-733b-43c8-99c3-f1dde30536fe",
              "name": "vol simple snapshot"
            },
            "creation_date": "2014-05-22T12:11:06.055998+00:00",
            "id": "6f418e5f-b42d-4423-a0b5-349c74c454a4",
            "name": "snapshot-0-1",
            "organization": "000a115d-2852-4b0a-9ce8-47f1134ba95a",
            "size": 10000000000,
            "state": "snapshotting",
            "volume_type": "l_ssd"
          }
        }

##### Update a snapshot [PUT]

Update details about a snapshot

The response is an object that has a key called `snapshot`. This key contain a standard `snapshot` object.

+ Parameters
    + snapshot_id: `6f418e5f-b42d-4423-a0b5-349c74c454a4`(required, string) - Snapshot unique identifier


+ Attributes
    + name: `snapshot-0-1` (required, string) - Snapshot name

+ Request (application/json)

    + Body

            {
                "name": "snapshot-0-1"
            }


+ Response 200 (application/json)

        {
          "snapshot": {
            "base_volume": {
              "id": "09a4184c-733b-43c8-99c3-f1dde30536fe",
              "name": "vol simple snapshot"
            },
            "creation_date": "2014-05-22T12:11:06.055998+00:00",
            "id": "6f418e5f-b42d-4423-a0b5-349c74c454a4",
            "name": "snapshot-0-1",
            "organization": "000a115d-2852-4b0a-9ce8-47f1134ba95a",
            "size": 10000000000,
            "state": "snapshotting",
            "volume_type": "l_ssd"
          }
        }

##### Remove a snapshot [DELETE]

Delete a snapshot

The response code is a 204, which means that the action was successful with no returned body data.

+ Response 204

