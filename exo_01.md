1. Récupérer tous les albums

Requête SQL

    SELECT albums.Title FROM albums

Réponse obtenue

    For Those About To Rock We Salute You
    Balls to the Wall
    Restless and Wild
    Let There Be Rock
    Big Ones
    Jagged Little Pill
    Facelift
    Warner 25 Anos
    Plays Metallica By Four Cellos
    Audioslave
    ...

2. Récupérer tous les albums dont le titre contient "Great"

Requête SQL

    SELECT albums.Title 
    FROM albums 
    WHERE albums.Title LIKE '%Great%'

Réponse obtenue

    Greatest Hits II
    Greatest Kiss
    Vault: Def Leppard's Greatest Hits
    Greatest Hits
    Motley Crue Greatest Hits
    Greatest Hits I
    Rotten Apples: Greatest Hits
    The Police Greatest Hits
    Great Opera Choruses
    Great Performances - Barber's Adagio and Other Romantic Favorites for Strings
    Great Recordings of the Century - Mahler: Das Lied von der Erde
    Great Recordings of the Century: Paganini's 24 Caprices
    Great Recordings of the Century - Shubert: Schwanengesang, 4 Lieder

3. Donner le nombre total d'albums contenus dans la base (sans regarder les id bien sûr)

Requête SQL

    SELECT COUNT( * ) FROM albums

Réponse obtenue

    347

4. Supprimer tous les albums dont le nom contient "music"

Requête SQL

    SELECT albums.Title 
    FROM albums 
    WHERE albums.Title LIKE '%music%'

Réponse obtenue

    343 résultats affichés / 347
      ALL expect 
    Handel: Music for the Royal Fireworks (Original Version 1749)
    Armada: Music from the Courts of England and Spain
    Purcell: Music for the Queen Mary
    Mozart: Chamber Music

5. Récupérer tous les albums écrits par AC/DC

Requête SQL

    SELECT 
      albums.Title,
      artists.Name
    FROM albums, artists
    WHERE
      albums.ArtistId = artists.ArtistId AND
      artists.Name = 'AC/DC'

Réponse obtenue

    For Those About To Rock We Salute You AC/DC
    Let There Be Rock AC/DC

6. Récupérer tous les titres des albums de AC/DC

Requête SQL

    SELECT tracks.Name
    FROM albums, artists, tracks
    WHERE
      albums.ArtistId = artists.ArtistId AND
      artists.Name = 'AC/DC' AND
      albums.AlbumId = tracks.AlbumId

Réponse obtenue

    For Those About To Rock (We Salute You)
    Put The Finger On You
    Let's Get It Up
    Inject The Venom
    Snowballed
    Evil Walks
    C.O.D.
    Breaking The Rules
    Night Of The Long Knives
    Spellbound
    Go Down
    Dog Eat Dog
    Let There Be Rock
    Bad Boy Boogie
    Problem Child
    Overdose
    Hell Ain't A Bad Place To Be
    Whole Lotta Rosie

7. Récupérer la liste des titres de l'album "Let There Be Rock"

Requête SQL

    SELECT tracks.Name
    FROM albums, artists, tracks
    WHERE
      albums.ArtistId = artists.ArtistId AND
      artists.Name = 'AC/DC' AND
      albums.AlbumId = tracks.AlbumId
      albums.AlbumId = 4 dans WHERE

Réponse obtenue

    Go Down
    Dog Eat Dog
    Let There Be Rock
    Bad Boy Boogie
    Problem Child
    Overdose
    Hell Ain't A Bad Place To Be
    Whole Lotta Rosie

8. Afficher le prix de cet album ainsi que sa durée totale

Requête SQL

    SELECT 
      albums.Title,
      sum (tracks.UnitPrice),
      sum (tracks.Milliseconds)
    FROM albums, artists, tracks
    WHERE
      albums.ArtistId = artists.ArtistId AND
      artists.Name = 'AC/DC' AND
      albums.AlbumId = tracks.AlbumId and
      albums.AlbumId = 4
    GROUP BY albums.AlbumId

Réponse obtenue

    Let There Be Rock 7.92  2453259

9. Afficher le coût de l'intégralité de la discographie de "Deep Purple"

Requête SQL

    SELECT 
      sum (tracks.UnitPrice)
    FROM albums, artists, tracks
    WHERE
      albums.ArtistId = artists.ArtistId AND
      artists.Name = 'Deep Purple' AND
      albums.AlbumId = tracks.AlbumId
    
GROUP BY albums.AlbumId

Réponse obtenue

    91.0799999999999

10. Créer l'album de ton artiste favori en base, en renseignant correctement les trois tables albums, artists et tracks

Requête SQL

    SELECT 
      artists.Name,
      tracks.Name
    FROM albums, artists, tracks
    WHERE
      albums.ArtistId = artists.ArtistId AND
      artists.Name = 'Nirvana' and
      (tracks.Name = 'Drain You' or
      tracks.Name = 'Smells Like Teen Spirit' or
      tracks.Name = 'Polly' or
      tracks.Name = 'Come As You Are' or
      tracks.Name = 'On A Plain')
    GROUP BY tracks.Name

Réponse obtenue

    Nirvana Come As You Are
    Nirvana Drain You
    Nirvana On A Plain
    Nirvana Polly
    Nirvana Smells Like Teen Spirit