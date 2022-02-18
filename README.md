# mysql-assignment1

CREATE TABLE `trainer_info` (
  `Trainer_Id` varchar(20) DEFAULT NULL,
  `Salutation` varchar(7) DEFAULT NULL,
  `Trainer_Name` varchar(30) DEFAULT NULL,
  `Trainer_location` varchar(30) DEFAULT NULL,
  `Trainer_Track` varchar(30) DEFAULT NULL,
  `Trainer_Qualification` varchar(100) DEFAULT NULL,
  `Trainer_Experience` int DEFAULT NULL,
  `Trainer_Email` varchar(100) DEFAULT NULL,
  `Trainer_Password` varchar(20) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
CREATE TABLE `trainer_feedback` (
  `Trainer_Id` varchar(20) NOT NULL,
  `Question_Id` varchar(45) DEFAULT NULL,
  `Batch_Iid` varchar(45) DEFAULT NULL,
  `Module_id` varchar(45) DEFAULT NULL,
  `Trainer_rating` int DEFAULT NULL,
  PRIMARY KEY (`Trainer_Id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
CREATE TABLE `questions` (
  `Question_Id` varchar(20) NOT NULL,
  `Module_id` varchar(45) DEFAULT NULL,
  `Question_Text` varchar(900) DEFAULT NULL,
  PRIMARY KEY (`Question_Id`),
  KEY `forignkey moduleId_idx` (`Module_id`),
  CONSTRAINT `forignkey moduleId` FOREIGN KEY (`Module_id`) REFERENCES `module_info` (`Module_Id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
CREATE TABLE `module_info` (
  `Module_Id` varchar(20) NOT NULL,
  `Module_Name` varchar(45) DEFAULT NULL,
  `Module_Duration` int DEFAULT NULL,
  PRIMARY KEY (`Module_Id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
CREATE TABLE `login_details` (
  `User_id` varchar(20) NOT NULL,
  `User_password` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`User_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
CREATE TABLE `batch_info` (
  `batch_Id` varchar(30) NOT NULL,
  `Batch_owner` varchar(45) DEFAULT NULL,
  `Batch_BU_Name` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`batch_Id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
CREATE TABLE `associate_status` (
  `Associate_Id` varchar(20) NOT NULL,
  `Module_id` varchar(45) DEFAULT NULL,
  `Start_Date` varchar(45) DEFAULT NULL,
  `End_Date` varchar(45) DEFAULT NULL,
  `AFeedbackGiven` varchar(45) DEFAULT NULL,
  `TFeedbackGiven` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`Associate_Id`),
  KEY `tomodule_idx` (`Module_id`),
  CONSTRAINT `tomodule` FOREIGN KEY (`Module_id`) REFERENCES `module_info` (`Module_Id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
CREATE TABLE `associate_info` (
  `Associate_Id` int NOT NULL,
  `Salutation` varchar(45) DEFAULT NULL,
  `Associate_name` varchar(45) DEFAULT NULL,
  `Associate_Location` varchar(45) DEFAULT NULL,
  `Associate_Track` varchar(45) DEFAULT NULL,
  `Associate_Qualification` varchar(45) DEFAULT NULL,
  `Associate_Email` varchar(45) DEFAULT NULL,
  `Associate_Password` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`Associate_Id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
CREATE TABLE `associate feedback` (
  `Associate_id` varchar(20) NOT NULL,
  `Question_id` varchar(45) DEFAULT NULL,
  `Module_id` varchar(45) DEFAULT NULL,
  `AssociAssociate_Rating` varchar(45) DEFAULT NULL,
  `Associate feedbackcol` int DEFAULT NULL,
  PRIMARY KEY (`Associate_id`),
  KEY `toquestion_idx` (`Question_id`),
  KEY `moduleto_idx` (`Module_id`),
  CONSTRAINT `moduleto` FOREIGN KEY (`Module_id`) REFERENCES `module_info` (`Module_Id`),
  CONSTRAINT `toquestion` FOREIGN KEY (`Question_id`) REFERENCES `questions` (`Question_Id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci;
