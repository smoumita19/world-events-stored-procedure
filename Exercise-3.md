3) Using the tblAuthor and tblEpisode tables, create a stored procedure called spMoffats to list out the 32 episodes written by Steven Moffat in date order (with the most recent first).

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
  -- Description:	This exercise will find the episodes which are written by Steven Moffat
  -- =============================================
  CREATE PROCEDURE spMoffats
  AS
    SELECT  epi.Title, aut.AuthorName
    FROM tblEpisode epi
    INNER JOIN tblAuthor aut
    ON aut.AuthorId = epi.AuthorId
    WHERE aut.AuthorName = 'Steven Moffat'
    ORDER BY epi.EpisodeDate DESC
  GO


</pre>
