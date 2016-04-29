# nerual
A command line tool used for sorting and managing media files.

##Usage
    nerual <options>        Basic syntax
    nerual --help -h        Display help
    nerual --config <file>  Define a configuration file


##Learning about a file

######Given an only file :

    Triassic.Park.1997.720p.WEBRip.2CH.x265.HEVC-PSA.mkv

######In a directory :

    Downloads

######To learn about the file :

    cd Downloads
    nerual

######Should yield :

    Target => Downloads
        ID        => Triassic.Park.1997.720p.WEBRip.2CH.x265.HEVC-PSA.mkv
        Name      => Triassic Park
        FileName  => TriassicPark
        Year      => 1997
        Genre     => Action
        Category  => Movie
        Format    => 720p
        Channels  => 2
        Codec     => HEVC-PSA
        Encoding  => x265
        Type      => mkv



##Configuring nerual

######Given a configuration file /etc/nerual.conf :

    [System]
        MovieDir       = /data/Movies
        MusicDir       = /data/Music
        ShowsDir       = /data/Shows
    [Settings]
        Sources        = /data,/home/user/Downloads
        OnSort         = Move
       #OnSort         = Copy
    [ThisApi]
        Enable         = true
        ThisApiKey     = 123abc456def
        ThisApiSecret  = p4ssw0rd
    [ThatApi]
        Enable         = false
        ThatApiKey     = 789ghi123jkl
        ThatApiSecret  = s3cr3t

######And using it :

    nerual --config /etc/nerual.conf

###### Should :

    1. Use ThisApi to find meta information about the file(s) listed in Settings.Sources
    2. Match on ThisApi and Move from the Settings.Sources directory to the configured System.$TypeDir directory.
        a. Movies to MovieDir
        b. Music  to MusicDir
        c. etc..
    3. Name the file the proposed FileName tag in the new directory


