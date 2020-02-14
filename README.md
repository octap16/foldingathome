# foldingathome


## sql script

>CREATE SCHEMA IF NOT EXISTS `folding_home_db` DEFAULT CHARACTER SET utf8 ;
>USE `folding_home_db` ;
>
>-- -----------------------------------------------------
>-- Table `folding_home_db`.`donors`
>-- -----------------------------------------------------
>CREATE TABLE IF NOT EXISTS `folding_home_db`.`donors` (
>  `id` INT(11) NOT NULL AUTO_INCREMENT,
>  `name` VARCHAR(1000) NOT NULL,
>  PRIMARY KEY (`id`),
>  UNIQUE INDEX `name` (`name` ASC) VISIBLE)
>ENGINE = InnoDB
>AUTO_INCREMENT = 3327075
>DEFAULT CHARACTER SET = utf8;
>
>
>-- -----------------------------------------------------
>-- Table `folding_home_db`.`donor_statistics`
>-- -----------------------------------------------------
>CREATE TABLE IF NOT EXISTS `folding_home_db`.`donor_statistics` (
>  `id` INT(11) NOT NULL AUTO_INCREMENT,
>  `wu` INT(11) NULL DEFAULT NULL,
>  `score` BIGINT(255) NULL DEFAULT NULL,
>  `rank` INT(11) NULL DEFAULT NULL,
>  `donor_statistic_date` DATE NULL DEFAULT NULL,
>  `donors_id` INT(11) NOT NULL,
>  PRIMARY KEY (`id`, `donors_id`),
>  UNIQUE INDEX `id_UNIQUE` (`id` ASC) VISIBLE,
>  INDEX `fk_donor_statistics_donors1_idx` (`donors_id` ASC) VISIBLE,
>  CONSTRAINT `fk_donor_statistics_donors1`
>    FOREIGN KEY (`donors_id`)
>    REFERENCES `folding_home_db`.`donors` (`id`))
>ENGINE = InnoDB
>AUTO_INCREMENT = 896266
>DEFAULT CHARACTER SET = utf8;
>
>
>-- -----------------------------------------------------
>-- Table `folding_home_db`.`teams`
>-- -----------------------------------------------------
>CREATE TABLE IF NOT EXISTS `folding_home_db`.`teams` (
>  `id` INT(11) NOT NULL,
>  `name` VARCHAR(200) NULL DEFAULT NULL,
>  PRIMARY KEY (`id`))
>ENGINE = InnoDB
>DEFAULT CHARACTER SET = utf8;
>
>
>-- -----------------------------------------------------
>-- Table `folding_home_db`.`donors_teams`
>-- -----------------------------------------------------
>CREATE TABLE IF NOT EXISTS `folding_home_db`.`donors_teams` (
>  `donors_id` INT(11) NOT NULL,
>  `teams_id` INT(11) NOT NULL,
>  PRIMARY KEY (`donors_id`, `teams_id`),
>  INDEX `fk_donors_has_teams_teams1_idx` (`teams_id` ASC) VISIBLE,
>  INDEX `fk_donors_has_teams_donors1_idx` (`donors_id` ASC) VISIBLE,
>  CONSTRAINT `fk_donors_has_teams_donors1`
>    FOREIGN KEY (`donors_id`)
>    REFERENCES `folding_home_db`.`donors` (`id`),
>  CONSTRAINT `fk_donors_has_teams_teams1`
>    FOREIGN KEY (`teams_id`)
>    REFERENCES `folding_home_db`.`teams` (`id`))
>ENGINE = InnoDB
>DEFAULT CHARACTER SET = utf8;
>
>
>-- -----------------------------------------------------
>-- Table `folding_home_db`.`team_statistics`
>-- -----------------------------------------------------
>CREATE TABLE IF NOT EXISTS `folding_home_db`.`team_statistics` (
>  `id` INT(11) NOT NULL AUTO_INCREMENT,
>  `wu` INT(11) NULL DEFAULT NULL,
>  `score` BIGINT(255) NULL DEFAULT NULL,
>  `rank` INT(11) NULL DEFAULT NULL,
>  `team_statistic_date` DATE NULL DEFAULT NULL,
>  `teams_id` INT(11) NOT NULL,
>  PRIMARY KEY (`id`, `teams_id`),
>  UNIQUE INDEX `id_UNIQUE` (`id` ASC) VISIBLE,
>  INDEX `fk_team_statistics_teams1_idx` (`teams_id` ASC) VISIBLE,
>  CONSTRAINT `fk_team_statistics_teams1`
>    FOREIGN KEY (`teams_id`)
>    REFERENCES `folding_home_db`.`teams` (`id`)
>    ON DELETE CASCADE
>    ON UPDATE CASCADE)
>ENGINE = InnoDB
>DEFAULT CHARACTER SET = utf8;
>
>
>SET SQL_MODE=@OLD_SQL_MODE;
>SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
>SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;


