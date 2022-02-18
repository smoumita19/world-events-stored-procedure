1) Create a stored procedure called uspCountriesAsia to list out all the countries with ContinentId equal to 1, in alphabetical order.
<pre>
  Solution:
  
  -- ================================================
  --
  -- ================================================
  SET ANSI_NULLS ON
  GO
  SET QUOTED_IDENTIFIER ON
  GO
  -- =============================================
  -- Author:		Moumita Sen
  -- Create date: 17/02/2022
  -- Description:	This sp will find all the countries with ContinentId equal to 1, in alphabetical order
  -- =============================================
  CREATE PROCEDURE uspCountriesAsia
  AS
    -- SET NOCOUNT ON added to prevent extra result sets from
    -- interfering with SELECT statements.
    SET NOCOUNT ON;

      -- Insert statements for procedure here
    SELECT c.CountryId, c.CountryName
    FROM tblCountry c
    WHERE c.ContinentId = 1
    ORDER BY c.CountryName
  GO

  
</pre>
