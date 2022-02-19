5) Run your stored procedure to show that it lists out 44 films.  
Now change your script so that it alters the stored procedure to list out only
those episodes featuring Matt Smith made in 2012, using this syntax in the WHERE clause:

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
  -- Description:	This exercise will find the episodes where Doctor's name is Matt Smith and which is released in 2012
  -- =============================================
  CREATE PROCEDURE spMathhSmithEpisodes
  AS
    -- SET NOCOUNT ON added to prevent extra result sets from
    -- interfering with SELECT statements.
    SET NOCOUNT ON;

      -- Insert statements for procedure here
    SELECT epi.SeriesNumber, epi.EpisodeNumber, epi.Title , epi.EpisodeDate, doc.DoctorName
    FROM tblEpisode epi
    INNER JOIN tblDoctor doc
    ON epi.DoctorId = doc.DoctorId
    WHERE doc.DoctorName = 'Matt Smith'
    AND YEAR(epi.EpisodeDate) = 2012

  GO

  
</pre>

