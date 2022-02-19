4) Create a different stored procedure called spRussell, listing out the 30 episodes penned by people called Russell.

<pre>
  Solution:
  -- ================================================
  -- ================================================
  SET ANSI_NULLS ON
  GO
  SET QUOTED_IDENTIFIER ON
  GO
  -- =============================================
  -- Author:		Moumita Sen
  -- Create date: 19/02/2022
  -- Description:	This exercise will find the episodes whose author is Russell T. Davies
  -- =============================================
  CREATE PROCEDURE spRussell
  AS
    -- SET NOCOUNT ON added to prevent extra result sets from
    -- interfering with SELECT statements.
    SET NOCOUNT ON;

    SELECT epi.Title 
    FROM tblEpisode epi
    INNER JOIN tblAuthor aut
    ON epi.AuthorId = aut.AuthorId
    WHERE aut.AuthorName LIKE 'Russell%'
    ORDER BY epi.EpisodeDate
  GO

</pre>
