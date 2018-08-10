# SimuroSot5-logs
SimuroSot5 log files of FIRA2018 TW

The meanings of a log file name are listed as follow, for example, 

20180620111606-5-TeamYellow-TeamBlue.rlg:

20180620111606 shows the date and time of the game;

5 shows it is the SimuroSot5 category;

TeamYellow shows the name of yellow team;

TeamBlue shows the name of blue team.


The contents of log file are the stream of LogEnvironment variables, which are 
put into log file cycle by cycle in binary mode.
The C++ code shows as follow:
//---------------------------------------------------
ofstream fout;
fout.open(strFile, ios_base::out | ios_base::binary);
//=====================================================

//---------------------------------------------------
LogEnvironment logEnv;
fout.write((char*)&logEnv, sizeof(LogEnvironment));
//=====================================================

//---------------------------------------------------
typedef struct
{
	double x, y, z;
} Vector3D;

typedef struct
{
	Vector3D pos;
	double rotation;
} LogRobot;

typedef struct
{
	LogRobot blueRobot[5];
	LogRobot yellowRobot[5];
	Vector3D currentBall;	
	long gameState;
	long whosBall;
} LogEnvironment;
//=====================================================
