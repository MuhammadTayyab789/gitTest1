DECLARE 
    @CNICFront VARBINARY(MAX),
    @CNICBack VARBINARY(MAX);

SELECT @CNICFront = BulkColumn
FROM OPENROWSET(BULK 'C:\Temp\cnic_front.jpg', SINGLE_BLOB) a;

SELECT @CNICBack = BulkColumn
FROM OPENROWSET(BULK 'C:\Temp\cnic_back.jpg', SINGLE_BLOB) b;

EXEC sp_Alfacustomerpostdata
    @Sessionid = 9876,
    @IDFrontImage = @CNICFront,
    @IDBackImage = @CNICBack,
    @CNIC_F_File_Name = '9876_CNIC_F.jpg',
    @CNIC_B_File_Name = '9876_CNIC_B.jpg',
    @CNIC_F_File_ContentType = 'image/jpeg',
    @CNIC_B_File_ContentType = 'image/jpeg';